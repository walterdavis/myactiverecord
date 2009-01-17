MyActiveRecord was created by Jake Grimley at MadeMedia Ltd. I have forked the project, with Jake's blessing, because he no longer has time to devote to upgrades and maintenance.

You may read more about MAR here: <http://www.phpclasses.org/browse/package/2990.html>

##MyActiveRecord

A simple, speedy Object/Relational Mapper for MySQL based on Martin 
Fowler's ActiveRecord pattern and heavily influenced by the implementation 
of the same name in Ruby on Rails.

###Features

* Mapping of table to class and row to object
* Relationship retrieval
* Data validation and error handling
* PHP5 and PHP4 compatibility

###License

**Copyright (c) 2006, Jake Grimley  <jake.grimley@mademedia.co.uk>
All rights reserved.**

Redistribution and use in source and binary forms, with or without 
modification, are permitted provided that the following conditions are met:

* Redistributions of source code must retain the above copyright notice, 
this list of conditions and the following disclaimer.

* Redistributions in binary form must reproduce the above copyright 
notice, this list of conditions and the following disclaimer in the 
documentation and/or other materials provided with the distribution.

* Neither the name of Made Media Ltd. nor the names of its contributors 
may be used to endorse or promote products derived from this 
software without specific prior written permission.

**THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS 
IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, 
THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR 
PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR 
CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, 
EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, 
PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR 
PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF 
LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING 
NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS 
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.**

###Limitations

This class acheives simplicty of use and implementation through the following 'by-design' limitations:

1. This class talks to MySQL only.

2. Table/Class mapping is achieved by each database table being named IDENTICALLY to the MyActiveRecord subclass that will represent it (but in lowercase for compatibility reasons).

3. Every database table mapped by MyActiveRecord MUST have an auto-incrementing primary-key named `id`.

###Changelog 0.3 - 0.4

1. BUG FIXES
    1.  Error is triggered when connection fails or database cannot be selected
    2.  If Class cannot be found or table cannot be found to match class scriptreports error instead of hanging. (this fixes bug introduced in 0.3)
    3. Removal of error notices on save dues to presumption about existance of variables

2. FIND_CHILDREN() IMPROVEMENTS  
Added new paramaters to the find_children() method. First the full 
complement of Where, OrderBy, Limit and Offset a-la FindAll(). Second, the 
addition of a ForeignKey parameter. Useful if you have a table with a
two foreign keys pointing to the same table, and so you need to use a 
different name to parent_table_id

3. ADDED FREQDIST() WHERE and LIMIT parameters  
e.g. `print_r( MyActiveRecord::FreqDist( 'Order', 'total_lines', "date BETWEEN '2005-01-01' AND '2006-01-01'" ) )`