# W-10381207 - Formula field showing different values in lex vs classic (and SOQL query)
# Repro
- Deploy the formulas here to a new org
- Create an Account and set the Days field value to "N/A"
- Look at the TestFormula checkbox field, it will be checked in Classic.
- - It will be unchecked in Lightning
- - It will be false in a SOQL query

Expected result is that it should be true/checked, but there is a bug in the shortcircuit '&&' logic.  Take a close look at the TestFormula fields, where this formula should shortcircuit after the firest expression is false:

Days__c != 'N/A' && VALUE(Days__c) > 0

More discussion in the Investigation
