# Data log item operations

_Operations that targets the items in a data-log_

## Information
The job is designed so that you should find the logs you're looking for, or a wider search.  
Followed by a filter-stage where you may filter out the more precise items you need to operate on.  
The operations that can be performed on data log items are performed on the results after find- and filter- stages.
In the store step you can control for example if the changes should be persisted or just saved as resource in the current workflow context.  

Examples for the filters:  

         * LeftSide: item.metadata.val1
         * Operator: ==
         * RightSide: hejsan
          
         * LeftSide: [rndnum(1,10)]
         * Operator: >
         * RightSide: 7
          
         * LeftSide: item.phone
         * Operator: ==
         * RightSide: incomingmessage.sender
         
         * LeftSide: metadata.incomingmessage-keyword
         * Operator: contains
         * RightSide: item.metadata.key


## Connections

This job can be connected to the following workflow elements.

* Jobs

## Requirements

* Fields marked with `*` require input.
* You need to ad the prefix `metadata.` to access data in your WFC

## Other

No further information available.
