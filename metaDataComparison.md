# Comparing MetaData  #

*MetaData can be compared in different ways depending on what type of metadata that can be identified.*

**This documentation is just a place holder**

Below is the different aliases:  
Use the value to the left e.g.  **{ "equals", "Equals" },** means that you can write equals **or** the **=** as operator, and both of them will be interpreted as a tests where we want both sides to be equal.
            // Equals
            { "equals", "Equals" },
            { "=", "Equals" },

            // Equals (Case-sensitive)
            { "==", "Case_sensitive Equals" },

            // Between
            { "between", "Between" },
            { "!between", "Not Between" },
            { "not between", "Not Between" },
            { "notbetween", "Not Between" },

            // Betweennumber (unique for comparing number)
            { "betweennumber", "Between number" },
            { "!betweennumber", "Not Between number" },
            { "notbetweennumber", "Not Between number" },
            { "not between number", "Not Between number" },

            // Is in
            { "isin", "Is in" },
            { "is in", "Is in" },

            // Is in
            { "notin", "Is not in" },
            { "is not in", "Is not in" },
            { "isnotin", "Is not in" },

            // Short-cuts for date-time
            { "before", "Before" },
            { "after", "After" },

            // Less than
            { "<", "Less than" },
             // TODO ? 
            //{ "lt", "lessthan" },

            // Less than or equals
            { "<=", "Less than or equals" },
            { "=<", "Less than or equals" },
            
            // Greater than
            { ">", "Greater than" },

            // Greater than or equals
            { ">=", "Greater than or equals" },
            { "=>", "Greater than or equals" },
            
            // Start with
            { "startswith", "Starts with" },
            // Start with (case sensitive)
            { "startswithcase", "Case_sensitive Starts with" },

            // Doesn't start with
            { "!startswith", "Not starts with" },
            { "not startswith", "Not starts with" },
            { "notstartswith", "Not starts with" },

            // Doesn't start with (case sensitive)
            { "!startswithcase", "Case_sensitive Not starts with" },
            { "not startswithcase", "Case_sensitive Not starts with" },
            { "notstartswithcase", "Case_sensitive Not starts with" },


            // Ends with
            { "endswith", "Ends with" },
            // Start with (case sensitive)
            { "endswithcase", "Case_sensitive Ends with" },

            // Doesn't end with
            { "!endswith", "Not ends with" },
            { "not endswith", "Not ends with" },
            // Doesn't end with (case sensitive)
            { "!endswithcase", "Case_sensitive Not end with" },
            { "not endswithcase", "Case_sensitive Not end with" },
            
            // Contains
            { "contains", "Contains" },
            // Contains (case sensitive)
            { "containscase", "Case_sensitive contains" },

            // Not Contains
            { "!contains", "Not contains" },
            { "not contains", "Not contains" },
            { "notcontains", "Not contains" },
            // Not Contains (case sensitive)
            { "!containscase", "Case_sensitive Not contains" },
            { "not containscase", "Case_sensitive Not contains" },
            { "notcontainscase", "Case_sensitive Not contains" },

            // Is empty
            { "is empty", "Empty" },
            { "isempty", "Empty" },
            { "empty", "Empty" },
            // Not Contains (case sensitive)
            { "not empty", "Not Empty" },
            { "notempty", "Not Empty" },
            { "!empty", "Not Empty" },

            // Length
            { "length", "Length" },
            { "length<", "Length less than" },
            { "length>", "Length greater than" },
