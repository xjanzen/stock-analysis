# Stock Analysis

## Overview of Project
We're refactoring a previous excel sheet that allowed you to look at a set of stock data and analyse those stocks. We need to refactor the code to allow it to work more efficiently and only loop through the stock data once instead of going through all the data for every separate stock. This is to help our friend Steve expand on his previous ask of analyzing stocks to allow him to potentially look through more stock data faster and more efficiently than before.

## Results
### Timing
Before refactoring the code it would take anywhere from a couple seconds to sometimes going a little over 10 seconds. Now I have yet to run the code and have it take longer than 0.2 seconds, usually taking ~0.10-0.15 seconds. This should only get more noticeable the larger the data set gets:
|VBA Challenge 2017|VBA Challenge 2018|
|----|----|
|![VBA Challenge 2017](resources/VBA_Challenge_2017.png)|![VBA Challenge 2018](resources/VBA_Challenge_2018.png)|

### Code Changes
Before we had setup the code to run through an array of stock codes and for each stock it would run through all the stock data we had and return the relevant stock data to us. We used a nested for loop for this with the parent for loop going through the stock codes and the child loop going through the whole data set for each stock code:
```
    For i = 0 To 11
        'set variables for each loop through the rows
        totalVolume = 0
        ticker = tickers(i)
        
        'loop over all the rows, once for each ticker
        For j = 2 To RowCount
            Worksheets("2018").Activate
            
            If Cells(j, 1).Value = ticker Then
                'increase totalVolume if current ticker
                totalVolume = totalVolume + Cells(j, 8).Value
            End If

            If Cells(j, 1).Value = ticker And Cells(j - 1, 1).Value <> ticker Then
                'set starting price of current ticker
                startingPrice = Cells(j, 6).Value
            End If
    
            If Cells(j, 1).Value = ticker And Cells(j + 1, 1).Value <> ticker Then
                'set ending price of current ticker
                endingPrice = Cells(j, 6).Value
            End If
    
        Next j
        
    Worksheets("All Stocks Analysis").Activate
    Cells(4 + i, 1).Value = ticker
    Cells(4 + i, 2).Value = totalVolume
    Cells(4 + i, 3).Value = endingPrice / startingPrice - 1
    Next i
```
To speed this up and only require a single loop through all the data we changed the code to use arrays so we could loop through the arrays as we went through each row in the data and change the stock we were looking at depending on the row, storing each stocks data in the arrays as we went:
```
    For i = 2 To RowCount
    
        '3a) Increase volume for current ticker
        tickerVolumes(tickerIndex) = tickerVolumes(tickerIndex) + Cells(i, 8).Value
        
        '3b) Check if the current row is the first row with the selected tickerIndex.
        If Cells(i, 1).Value = tickers(tickerIndex) And Cells(i - 1, 1).Value <> tickers(tickerIndex) Then
            'if it matches set starting price
            tickerStartingPrices(tickerIndex) = Cells(i, 6).Value
        End If
        
        '3c) check if the current row is the last row with the selected ticker
        If Cells(i, 1).Value = tickers(tickerIndex) And Cells(i + 1, 1).Value <> tickers(tickerIndex) Then
            'if it's the last  row with the ticker, set the ending price
            tickerEndingPrices(tickerIndex) = Cells(i, 6).Value
            
            '3d) and increase the tickerIndex.
            tickerIndex = tickerIndex + 1
        End If
    
    Next i
```
And then we use a separate for loop to output the data we collected in the separate arrays

## Summary
### Advantages
- The process of refactoring the code
  - Pro: we can double check our code to make sure there are no mistakes
  - Pro: we can make sure we're using the fastest methods possible to do the required tasks and allow for expansion on the original data set
- Original Code
  - Pro: easy to setup and the logic is easy to follow in a step by step process
- Refactored code
  - Pro: runs very fast because it only needs to run through the data set once
  - Pro: a little easier to add more data and only needs to run through the new lines added

### Disadvantages
- The process of refactoring the code
  - Con: it can be difficult to find better/faster ways to do something when the current logic is there in front of you
  - Con: takes more time and ideally the person who initially setup the code included comments as code can be difficult to read otherwise
- Original Code
  - Con: takes a long time to run
  - Con: not very mutable, the more lines you add to the data set and the more stocks you want to check the longer it will take to run as the code will have to run through the whole data set for each new stock and for every line added your adding multiple lines the code has to run through since it goes through the whole data set multiple times
  - Con: depends on the sorting of the data set. If it's not in chronological order or the stock codes aren't grouped together it can mess up certain data like the Return
- Refactored code
  - Con: depends even more heavily than the original on the sorting of the data set. If it's not in chronological order or the stock codes aren't grouped together it will mess up almost all data points
  - Con: can be a little more difficult to follow the logic

### Conclusion
The disadvantage was already a problem in the original code while the advantage of this refactored code is very telling. It’s a large improvement in almost all cases this would be required.
