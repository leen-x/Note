
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>CONCAT</strong></p>
<p>语法： CONCAT（string1,string2）</p>
<p>功能：连接两个字符串</p>
<p>SQL&gt; select concat('010-','88888888')||'23'&nbsp; 连接 from dual;</p>
<p>&nbsp;</p>
<p>连接</p>
<p>010-8888888823</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>INITCAP</strong></p>
<p>语法：INITCAP（string）</p>
<p>功能：返回字符单词首字母大写，其余小写，单词用空格和非字母字符分隔。</p>
<p>SQL&gt; select initcap('smith hEllo') upp from dual;</p>
<p>&nbsp;</p>
<p>UPP</p>
<p>Smith Hello</p>
<p>&nbsp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>LOWER</strong></p>
<p>&nbsp;&nbsp;&nbsp; 语法：LOWER(string)</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp; 功能：所以字母小写</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp; SQL&gt; select lower('AaBbCcDd') AaBbCcDd from dual;</p>
<p>&nbsp;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp; AaBbCcDd</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp; aabbccdd</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>LPAD/RPAD</strong></p>
<p>语法：LPAD/RPAD（string1,x[,string2]）</p>
<p>功能：在string1字符左边或右边粘贴数个string2字符，直到字符总字节数达到x字节。string2默认为空格。</p>
<p>如果string2的长度要比X字符少，就按照需要进行复制。如果string2多于X字符，则仅string2前面的X各字符被使用。如果string1长度大于x,则返回string1左端x个字符。</p>
<p>&nbsp;</p>
<p>RPAD&nbsp; 在列的右边粘贴字符</p>
<p>LPAD&nbsp; 在列的左边粘贴字符</p>
<p>SQL&gt; select lpad(rpad('gao',10,'*'),17,'*')from dual;</p>
<p>&nbsp;</p>
<p>LPAD(RPAD('GAO',1</p>
<p>*******gao*******</p>
<p>不够字符则用*来填满</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>NLS_INITCAP</strong></p>
<p>语法：NLS_INITCAP（string[,nlsparams]）</p>
<p>功能：返回字符串每个单词第一个字母大写而单词中的其他字母小写的string，nlsparams</p>
<p>指定了不同于该会话缺省值的不同排序序列。如果不指定参数，则功能和INITCAP相同。Nlsparams可以使用的形式是：‘NLS_SORT=sort’ 这里sort制订了一个语言排序序列。</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>NLS_LOWER</strong></p>
<p>语法：NLS_LOWER（string[,nlsparams]）</p>
<p>功能：返回字符串中的所有字母都是小写形式的string。不是字母的字符不变。</p>
<p>Nlsparams参数的形式与用途和NLS_INITCAP中的nlsparams参数是相同的。如果nlsparams没有被包含，那么NLS_LOWER所作的处理和LOWER相同。</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>NLS_UPPER</strong></p>
<p>语法：NLS_UPPER（string[,nlsparams]）</p>
<p>功能：返回字符串中的所有字母都是大写的形式的string。不是字母的字符不变。nlsparams参数的形式与用途和NLS_INITCAP中的相同。如果没有设定参数，则NLS_UPPER功能和UPPER相同。</p>
<p>使用位置：过程性语句和SQL语句。</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>REGEXP_REPLACE</strong></p>
<p>语法：REGEXP_REPLACE(str1,pattem[,str2[,pos[,occ[,par]]]])</p>
<p>功能：10g新增函数，扩展了REPLACE函数的功能，并且用于按照特定正则表达式的规则替换字符串。其中参数str1指定源字符表达式，pattem指定正则表达式，str2指定替换字符串，pos指定起始搜索位置，occ指定替换出现的第几个字符串，par指定默认匹配操作的文本串。</p>
<p>&nbsp;</p>
<p>select REGEXP_REPLACE(a,’(.)’,’\1’) a from count;</p>
<p>A r g e n t i n a</p>
<p>&nbsp;</p>
<p>体会NVL为DECODE，只支持NVL()内不再有其它括号()</p>
<p>select a,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; instr(upper(a), 'NVL(', 1) a3,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; instr(upper(a), ')',instr(upper(a), 'NVL(', 1),1) a4,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; substr(a,instr(upper(a), 'NVL(', 1),instr(upper(a), ')',instr(upper(a), 'NVL(', 1),1)-instr(upper(a), 'NVL(', 1)+1) a41,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; substr(a,instr(upper(a), 'NVL(', 1)+4,instr(upper(a), ')',instr(upper(a), 'NVL(', 1), 1)-instr(upper(a), 'NVL(', 1)-4) a5,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; REGEXP_REPLACE(</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; substr(a,instr(upper(a), 'NVL(', 1)+4,instr(upper(a), ')',instr(upper(a), 'NVL(', 1), 1)-instr(upper(a), 'NVL(', 1)-4),</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; '(.*),(.*)','\2,\1'</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ) a6,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; REGEXP_REPLACE(</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; substr(a,instr(upper(a), 'NVL(', 1)+4,instr(upper(a), ')',instr(upper(a), 'NVL(', 1), 1)-instr(upper(a), 'NVL(', 1)-4),</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; '(.*),(.*)','decode(\1,null,\2,'''',\2,\1)'</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ) a7,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; substr(a,1,instr(upper(a), 'NVL(', 1)-1)||REGEXP_REPLACE(</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; substr(a,instr(upper(a), 'NVL(', 1)+4,instr(upper(a), ')',instr(upper(a), 'NVL(', 1), 1)-instr(upper(a), 'NVL(', 1)-4),</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; '(.*),(.*)','decode(\1,null,\2,'''',\2,\1)'</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; )||substr(a,instr(upper(a), ')',instr(upper(a), 'NVL(', 1), 1)+1) a8</p>
<p>&nbsp; from temp_liut a;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p>判断是否是数字</p>
<p>regexp_replace(a, '\d+', '') is null</p>
<p>&nbsp;</p>
<p><strong>REGEXP_SUBSTR</strong></p>
<p>语法：REGEXP_SUBSTR(str1,pattem [,pos[,occ[,par]]])</p>
<p>功能：10g新增函数，扩展了SUBSTR函数的功能，并且用于按照特定表达式的规则返回字符串的子串。其中参数str1指定源字符表达式，pattem指定规则表达式， pos指定起始搜索位置，occ指定替换出现的第几个字符串，par指定默认匹配操作的文本串。</p>
<p>&nbsp;</p>
<p>Select REGEXP_SUBSTR(‘http://www.oracle.com/products’,’http://([[:alnum:]]+\.?)’) a from dual;</p>
<p>&nbsp;</p>
<p>a</p>
<p>http://www.oracle.com/</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>REPLACE</strong></p>
<p>语法：REPLACE（string，search_str[,replace_str]）</p>
<p>功能：把string中的所有的子字符串search_str用可选的replace_str替换，如果没有指定replace_str，所有的string中的子字符串search_str都将被删除。REPLACE是TRANSLATE所提供的功能的一个子集。</p>
<p>&nbsp;</p>
<p>REPLACE('string','s1','s2')</p>
<p>string&nbsp;&nbsp; 希望被替换的字符或变量</p>
<p>s1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 被替换的字符串</p>
<p>s2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 要替换的字符串</p>
<p>SQL&gt; select replace('he lohe you','he','i') from dual;</p>
<p>&nbsp;</p>
<p>replace('he lohe you','he','i')</p>
<p>i loi you</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TRIM/LTRIM/RTRIM</strong></p>
<p>语法1：LTRIM/RTRIM（string1,[string2]）</p>
<p>语法2：trim([string2] from string1)</p>
<p>语法1功能：中删除从左/右边算起出现在string1中的字符string2，string2如果是多个字符则逐个单字符比对删除,tring2被缺省设置为单个的空格。当遇到不在string2中的第一个字符，结果就被返回了；</p>
<p>语法2功能：删除左右两边出现在string1中的字符string2，tring2必须为单字符，否则报错。</p>
<p>&nbsp;</p>
<p>select ltrim(rtrim('&nbsp;&nbsp; gao qian jing&nbsp;&nbsp; ',' '),' ') from dual;</p>
<p>gao qian jing</p>
<p>&nbsp;</p>
<p>select ltrim('abaaaabbbcda','ab') from dual;</p>
<p>cda</p>
<p>&nbsp;</p>
<p>select trim('a' from 'abacda') from dual;</p>
<p>bacd</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>SOUNDEX</strong></p>
<p>语法:&nbsp; SOUNDEX（string）</p>
<p>功能:&nbsp; 返回string的声音表示形式.这对于比较两个拼写不同但是发音类似的单词而言很有帮助，如果字符发音相同，则返回的结果会一致.</p>
<p>&nbsp;</p>
<p>SOUNDEX 返回一个与给定的字符串读音相同的字符串</p>
<p>SQL&gt; create table table1(xm varchar(8));</p>
<p>SQL&gt; insert into table1 values('weather');</p>
<p>SQL&gt; insert into table1 values('wether');</p>
<p>SQL&gt; insert into table1 values('gao');</p>
<p>&nbsp;</p>
<p>SQL&gt; select xm from table1 where soundex(xm)=soundex('weather');</p>
<p>&nbsp;</p>
<p>XM</p>
<p>weather</p>
<p>wether</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>SUBSTR</strong></p>
<p>语法:&nbsp; SUBSTR（string,a[,b]）</p>
<p>功能：截取字符串，从第a个开始取b个字符，这个务必要注意，是字符。 vachar2最长4000个字节，GBK编码中一个中文字符占2个字节，韩文字符占4个字节，如果string是date或者number的数据类型，会自动转化为varchar2。</p>
<p>&nbsp;</p>
<p>SQL&gt; select substr('13088888888',3,8) 截取字符串 from dual;</p>
<p>截取字符串</p>
<p>08888888</p>
<p>&nbsp;</p>
<p>select SUBSTR(t.a,4),a from temp_liut t;</p>
<p>JAN-00&nbsp; 04-jan-00</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TRANSLATE</strong></p>
<p>语法:&nbsp; TRANSLATE(string,from_str,to_str)</p>
<p>功能:&nbsp; 将字符string按照from_str与to_str的对应规则进行处理，返回将所出现的from_str中的每个字符替换为to_str中的相应字符以后的string. TRANSLATE是REPLACE所提供的功能的一个超集.如果from_str比to_str长,那么在from_str中而不在to_str中而外的字符将从string中被删除,因为它们没有相应的替换字符. to_str不能为空.Oracle把空字符串认为是NULL,并且如果TRANSLATE中的任何参数为NULL,那么结果也是NULL.</p>
<p>&nbsp;</p>
<div>
<p>Select TRANSLATE('2abc2234','01234abcde','99999XXXXX') tra from dual</p>
<p>9XXX9999</p>
</div>
<p>&nbsp;</p>
<p>select replace(TRANSLATE('as中国fd1234','1234567890','0000000000'),'0') from dual;</p>
<p>&nbsp;</p>
<p>查找字符串',01234,2342,2,'中逗号出现次数</p>
<p>select length(translate(',01234,2342,2,', 'a0123456789', ' ')) from dual;</p>
<p>&nbsp;</p>
<p>判断字符串是否是数字</p>
<p>replace(translate(a, '0123456789', '0'),'0') is null</p>
<p>regexp_replace(a, '\d+', '') is null</p>
<p>&nbsp;</p>
<p><strong>UPPER</strong></p>
<p>语法: UPPER（string）</p>
<p>功能: 所有字母大写.（不是字母的字符不变.如果string是CHAR数据类型的,那么结果也是CHAR类型的.如果string是VARCHAR2类型的,那么结果也是VARCHAR2类型的）.</p>
<p>&nbsp;SQL&gt; select upper('AaBbCcDd') upper from dual;</p>
<p>&nbsp;</p>
<p>UPPER</p>
<p>AABBCCDD</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p align="center"><strong>F.2&nbsp;&nbsp;&nbsp; </strong><strong>字符函数——返回数字</strong></p>
<p>&nbsp;</p>
<p>(ascii,instr,instrb,length,lengthb,nls_sort)</p>
<p>&nbsp;</p>
<p>说明：可以sql和plsql中使用</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><strong>ASCII</strong></p>
<p>语法:&nbsp; ASCII（string）</p>
<p>功能: 返回string字符串首字符的十进制表示ascii码值。 CHR和ASCII是互为相反的函数.CHR得到给定字符编码的响应字符. ASCII得到给定字符的字符编码.</p>
<p>&nbsp;</p>
<p>SQL&gt; select ascii('A') A,ascii('a') a,ascii('0') zero,ascii(' ') space from dual;</p>
<p>&nbsp;</p>
<p>A&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; A&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ZERO&nbsp;&nbsp;&nbsp;&nbsp; SPACE</p>
<p>65&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 97&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 48&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 32</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>INSTR</strong></p>
<p>语法:&nbsp; INSTR（str1, str2[,a,b]）</p>
<p>功能:&nbsp; 得到在str1中包含str2的位置. a&gt;0,str1时从左边开始检查的,开始的位置为a;a&lt;0,那么str1是从右边开始进行扫描的,开始的位置为a。第b次出现的位置将被返回. a和b都缺省设置为1,这将会返回在string1中第一次出现string2的位置.如果string2在a和b的规定下没有找到,那么返回0.位置的计算是相对于string1的开始位置的,不管a和b的取值是多少.</p>
<p>&nbsp;</p>
<p>INSTR(C1,C2,I,J) 在一个字符串中搜索指定的字符,返回发现指定的字符的位置;</p>
<p>C1&nbsp;&nbsp;&nbsp; 被搜索的字符串</p>
<p>C2&nbsp;&nbsp;&nbsp; 希望搜索的字符串</p>
<p>I&nbsp;&nbsp;&nbsp;&nbsp; 搜索的开始位置,默认为1(如果为负数会从后向前搜索)</p>
<p>J&nbsp;&nbsp;&nbsp;&nbsp; 出现的位置,默认为1</p>
<p>SQL&gt; select instr('oracle traning','ra',1,2) instring from dual;</p>
<p>&nbsp;</p>
<p>INSTRING</p>
<p>9</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>INSTRB</strong></p>
<p>语法:&nbsp; INSTRB（string1, string2[a,[b]]）</p>
<p>功能:&nbsp; 和INSTR相同,只是操作的对参数字符使用的位置的是字节.</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>LENGTH</strong></p>
<p>语法:&nbsp; LENGTH（string）</p>
<p>功能:&nbsp; 返回字符串的长度，特别注意的，对于空的字段，返回为空，而不是0。</p>
<p>&nbsp;</p>
<p>SELECT&nbsp;&nbsp; LENGTH (' 130 ') 返回字符串长度&nbsp; FROM DUAL;</p>
<p>&nbsp;</p>
<p>返回字符串长度</p>
<p>5</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>LENGTHB</strong></p>
<p>语法:&nbsp; LENGTHB（string）</p>
<p>功能:&nbsp; 返回以字节为单位的string的长度.对于单字节字符集LENGTHB和LENGTH是一样的.</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>NLS_SORT</strong></p>
<p>语法: NLS_SORT（string[,nlsparams]）</p>
<p>功能: 得到用于排序string的字符串字节.所有的数值都被转换为字节字符串,这样在不同数据库之间就保持了一致性. Nlsparams的作用和NLS_INITCAP中的相同.如果忽略参数,会话使用缺省排序.</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p align="center"><strong>F.3&nbsp;&nbsp;&nbsp; </strong><strong>数学函数</strong></p>
<p>&nbsp;</p>
<p>(abs,acos,asin,atan,atan2,ceil,cos,cosh,exp,floor,ln,log,mod,power,round,sign,sin,sinh,sqrt,tan,tanh,trunc)</p>
<p>&nbsp;</p>
<p>说明：数学函数的输入和输出都是数字型，并且多数函数精确到38位。函数cos\cosh\exp\ln\log\sin\sinh\sqrt\tan\tanh精确到36位，acos\asin\atan\atan2精确到30为。数学函数可以在sql语句和plsql块中引用。</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><strong>ABS</strong></p>
<p>语法:&nbsp;&nbsp; ABS(x)</p>
<p>功能:&nbsp;&nbsp; 得到x的绝对值.</p>
<p>&nbsp;</p>
<p>SQL&gt; select abs(100),abs(-100) from dual;</p>
<p>&nbsp;</p>
<p>ABS(100) ABS(-100)</p>
<p>100&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 100</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>ACOS</strong></p>
<p>语法:&nbsp; ACOS(x)</p>
<p>功能:&nbsp; 返回x的反余弦值. 输入x应该从-1到1之间的数,结果在0到pi之间,输出以弧度为单位.</p>
<p>&nbsp;</p>
<p>SQL&gt; select acos(-1) from dual;</p>
<p>&nbsp;</p>
<p>ACOS(-1)</p>
<p>3.1415927</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>ASIN</strong></p>
<p>语法:&nbsp; ASIN(x)</p>
<p>功能:&nbsp; 返回x的反正弦值. X的范围应该是－1到1之间,返回的结果在－pi/2到pi/2之间,以弧度为单位.</p>
<p>&nbsp;</p>
<p>SQL&gt; select asin(0.5) from dual;</p>
<p>&nbsp;</p>
<p>ASIN(0.5)</p>
<p>.52359878</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>ATAN</strong></p>
<p>语法:&nbsp; ATAN(x)</p>
<p>功能:&nbsp; 计算x的反正切值.返回值在－pi/2到pi/2之间,单位是弧度.</p>
<p>&nbsp;</p>
<p>SQL&gt; select atan(1) from dual;</p>
<p>&nbsp;</p>
<p>ATAN(1)</p>
<p>.78539816</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>ATAN2</strong></p>
<p>语法:&nbsp; ATAN2(x,y)</p>
<p>功能: 返回x除以y的反正切值.结果在负的pi/2到正的pi/2之间,单位是弧度.</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>CEIL</strong></p>
<p>语法:&nbsp; CEIL(x)</p>
<p>功能:&nbsp; 计算大于或等于x的最小整数值.</p>
<p>&nbsp;</p>
<p>SQL&gt; select ceil(3.1415927) from dual;</p>
<p>&nbsp;</p>
<p>CEIL(3.1415927)</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 4</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>COS</strong></p>
<p>语法:&nbsp; COS(x)</p>
<p>功能:&nbsp; 返回x的余弦值. x的单位是弧度.</p>
<p>&nbsp;</p>
<p>SQL&gt; select cos(-3.1415927) from dual;</p>
<p>&nbsp;</p>
<p>COS(-3.1415927)</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp; -1</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>COSH</strong></p>
<p>语法:&nbsp; COSH(x)</p>
<p>功能:&nbsp; 计算x的双曲余弦值.</p>
<p>&nbsp;</p>
<p>SQL&gt; select cosh(20) from dual;</p>
<p>&nbsp;</p>
<p>COSH(20)</p>
<p>242582598</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>EXP</strong></p>
<p>语法:&nbsp; EXP(x)</p>
<p>功能:&nbsp; 计算e的x次幂. e为自然对数,约等于2.71828.</p>
<p>&nbsp;</p>
<p>SQL&gt; select exp(2),exp(1) from dual;</p>
<p>&nbsp;</p>
<p>EXP(2)&nbsp;&nbsp;&nbsp; EXP(1)</p>
<p>7.3890561 2.7182818</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>FLOOR</strong></p>
<p>语法:&nbsp; FLOOR(x)</p>
<p>功能:&nbsp; 返回小于等于x的最大整数值.</p>
<p>&nbsp;</p>
<p>SQL&gt; SELECT&nbsp;&nbsp; FLOOR (2345.67), FLOOR (-2345.67) FROM dual;</p>
<p>&nbsp;</p>
<p>FLOOR(2345.67)&nbsp;&nbsp; FLOOR (-2345.67)</p>
<p>&nbsp; 2345&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; -2346</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>LN</strong></p>
<p>语法:&nbsp; LN(x)</p>
<p>功能:&nbsp; 返回x的自然对数. x必须是正数,并且大于0</p>
<p>&nbsp;</p>
<p>SQL&gt; select ln(1),ln(2),ln(2.7182818) from dual;</p>
<p>&nbsp;</p>
<p>LN(1)&nbsp;&nbsp;&nbsp;&nbsp; LN(2) LN(2.7182818)</p>
<p>0 .69314718&nbsp;&nbsp;&nbsp;&nbsp; .99999999</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>LOG</strong></p>
<p>语法:&nbsp; LOG(x,y)</p>
<p>功能:&nbsp; 计算以x为底的y的对数.底必须大于0而且不等于1, y为任意正数.</p>
<p>&nbsp;</p>
<p>SQL&gt; select log(2,1),log(2,4) from dual;</p>
<p>&nbsp;</p>
<p>LOG(2,1)&nbsp; LOG(2,4)</p>
<p>0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>MOD</strong></p>
<p>语法:&nbsp; MOD(x,y)</p>
<p>功能:&nbsp; 返回x除以y的余数.如果y是0,则返回x</p>
<p>&nbsp;</p>
<p>SQL&gt; select mod(10,3),mod(3,3),mod(2,3) from dual;</p>
<p>&nbsp;</p>
<p>MOD(10,3)&nbsp; MOD(3,3)&nbsp; MOD(2,3)</p>
<p>1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>POWER</strong></p>
<p>语法:&nbsp; POWER(x,y)</p>
<p>功能:&nbsp; 计算x的y次幂.</p>
<p>&nbsp;</p>
<p>POWER 返回n1的n2次方根</p>
<p>SQL&gt; select power(2,10),power(3,3) from dual;</p>
<p>&nbsp;</p>
<p>POWER(2,10) POWER(3,3)</p>
<p>1024&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 27</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>ROUND</strong></p>
<p>语法:&nbsp; ROUND(x[,y])</p>
<p>功能:&nbsp; 四舍五入函数，y缺省值为0，x保留整数；y&gt;0，x保留小数点右边y位；y&lt;0，x保留小数点左边 |y| 位;可以对时间进行round，效果是只保留年月日。</p>
<p>&nbsp;</p>
<p>SELECT&nbsp;&nbsp; ROUND (55.655, 2),&nbsp;&nbsp; --55.66</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ROUND (55.654, 2),&nbsp;&nbsp; --55.65</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ROUND (45.654, -1),&nbsp; --50</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ROUND (45.654, -2),&nbsp; --0</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ROUND (55.654, -2)&nbsp;&nbsp; --100</p>
<p>&nbsp; FROM&nbsp;&nbsp; DUAL;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>SIGN</strong></p>
<p>语法:&nbsp; SIGN(x)</p>
<p>功能:&nbsp; 检测x的正负.如果x&lt;0返回－1.如果x=0返回0.如果x&gt;0返回1.</p>
<p>&nbsp;</p>
<p>SQL&gt; select sign(123),sign(-100),sign(0) from dual;</p>
<p>&nbsp;</p>
<p>SIGN(123) SIGN(-100)&nbsp;&nbsp; SIGN(0)</p>
<p>1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;-1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0</p>
<p>&nbsp;</p>
<p>常和decode 结合使用</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>SIN</strong></p>
<p>语法:SIN(x)</p>
<p>功能:计算x的正弦值. X是一个以弧度表示的角度.</p>
<p>&nbsp;</p>
<p>SQL&gt; select sin(1.57079) from dual;</p>
<p>&nbsp;</p>
<p>SIN(1.57079)</p>
<p>&nbsp;&nbsp; 1</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>SINH</strong></p>
<p>语法:SINH(x)</p>
<p>功能:返回x的双曲正弦值.</p>
<p>&nbsp;</p>
<p>SQL&gt; select sin(20),sinh(20) from dual;</p>
<p>&nbsp;</p>
<p>SIN(20)&nbsp; SINH(20)</p>
<p>.91294525 242582598</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>SQRT</strong></p>
<p>语法:&nbsp; SQRT(x)</p>
<p>功能:&nbsp; 返回x的平方根. x必须是正数.</p>
<p>&nbsp;</p>
<p>SQL&gt; select sqrt(64),sqrt(10) from dual;</p>
<p>&nbsp;</p>
<p>SQRT(64)&nbsp; SQRT(10)</p>
<p>8 3.1622777</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TAN</strong></p>
<p>语法:&nbsp; TAN(x)</p>
<p>功能:&nbsp; 计算x的正切值, x是一个以弧度位单位的角度.</p>
<p>&nbsp;</p>
<p>SQL&gt; select tan(20),tan(10) from dual;</p>
<p>&nbsp;</p>
<p>TAN(20)&nbsp;&nbsp; TAN(10)</p>
<p>2.2371609 .64836083</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TANH</strong></p>
<p>语法:&nbsp; TANH(x)</p>
<p>功能:&nbsp; 计算x的双曲正切值.</p>
<p>&nbsp;</p>
<p>SQL&gt; select tanh(20),tan(20) from dual;</p>
<p>&nbsp;</p>
<p>TANH(20)&nbsp;&nbsp; TAN(20)</p>
<p>1 2.2371609</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TRUNC</strong></p>
<p>语法:&nbsp; TRUNC(x[,y])</p>
<p>功能:&nbsp; 截取数字函数，只舍不入函数， y缺省值为0，x保留整数；y&gt;0，x保留小数点右边y位；y&lt;0，x保留小数点左边 |y| 位</p>
<p>&nbsp;</p>
<p>SELECT&nbsp;&nbsp; TRUNC (55.655, 2), &nbsp;&nbsp;--55.65</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; TRUNC (55.654, 2),&nbsp;&nbsp; --55.65</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; TRUNC (45.654, -1),&nbsp; --40</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; TRUNC (45.654, -2),&nbsp; --0</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; TRUNC (55.654, -2)&nbsp;&nbsp; --0</p>
<p>&nbsp; FROM&nbsp;&nbsp; DUAL;</p>
<p>&nbsp;</p>
<p>SELECT&nbsp;&nbsp; TRUNC (SYSDATE, 'DD'),&nbsp; --当天</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; TRUNC (SYSDATE, 'MM'),&nbsp; --本月第一天</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; TRUNC (SYSDATE, 'yyyy'),&nbsp; --本年第一天</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; TRUNC (SYSDATE, 'day'),&nbsp; --本周第一天</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; TRUNC (SYSDATE, 'q')&nbsp; --本季度第一天</p>
<p>&nbsp; FROM&nbsp;&nbsp; DUAL;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p align="center"><strong>F.4&nbsp; </strong><strong>日期时间函数</strong></p>
<p>(add_months,current_date,current_timestamp,dbtimesone,extract,from_tz,last_day,months_between,new_time,next_day,numtodsinternal,numtoyminternal,round,sys_extract_utc,sysdate,systimestamp,to_dsinternal,to_timestamp,to_timestamp_tz,to_yminternal,trunc,tz_offset)</p>
<p>&nbsp;</p>
<p>说明：日期时间函数用于处理date和timestamp类型的数据，除了函数months_between返回数字外，其余均返回date类型，Oracle以7位数字格式来存放日期数据，包括世纪、年、月、日、小时、分钟、秒，并且默认日期显式格式为“DD-MON-YY”。</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><strong>ADD_MONTHS</strong></p>
<p>语法:ADD_MONTHS(d,x)</p>
<p>功能:返回日期d加上x个月后的月份。x可以是任意整数。如果结果日期中的月份所包含的天数比d日期中的“日”分量要少。（即相加后的结果日期中的日分量信息已经超过该月的最后一天，例如，8月31日加上一个月之后得到9月31日，而9月只能有30天）返回结果月份的最后一天。</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>&nbsp;</p>
<p>SQL&gt; select to_char(add_months(to_date('199912','yyyymm'),2),'yyyymm') from dual;</p>
<p>TO_CHA</p>
<p>200002</p>
<p>&nbsp;</p>
<p>SQL&gt; select to_char(add_months(to_date('199912','yyyymm'),-2),'yyyymm') from dual;</p>
<p>TO_CHA</p>
<p>199910</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>CURRENT_DATE</strong></p>
<p>语法: CURRENT_DATE</p>
<p>功能:9i新增函数，返回当前会话时区所对应的日期时间。</p>
<p>&nbsp;</p>
<p>select CURRENT_DATE from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>CURRENT_TIMESTAMP</strong></p>
<p>语法:CURRENT_TIMESTAMP</p>
<p>功能:9i新增函数，返回当前会话时区所对应的日期时间。</p>
<p>&nbsp;</p>
<p>select CURRENT_TIMESTAMP from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>DBTIMESONE</strong></p>
<p>语法:DBTIMESONE</p>
<p>功能:9i新增函数，返回数据库所在时区。</p>
<p>&nbsp;</p>
<p>select DBTIMESONE from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>EXTRACT</strong></p>
<p>语法: EXTRACT(s)</p>
<p>功能:9i新增函数，从日期时间值中取得所需要的特定数据</p>
<p>&nbsp;</p>
<p>Select extract(year from sysdate) year from dual;</p>
<p>&nbsp;</p>
<p>Yaer</p>
<p>2013</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>FROM_TZ</strong></p>
<p>语法: FROM_TZ(s)</p>
<p>功能:9i新增函数，将特定时区的TIMESTAMP值转换为TIMESTAMP WITH TIME ZONE值。</p>
<p>&nbsp;</p>
<p>Select from_tz(timestamp ‘2013-03-28 08:00:00’,’3:00’);</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>LAST_DAY</strong></p>
<p>语法:LAST_DAY(d)</p>
<p>功能:计算包含日期的d的月份最后一天的日期.这个函数可以用来计算当月中剩余天数.</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>LAST_DAY</p>
<p>返回日期的最后一天</p>
<p>SQL&gt; select to_char(sysdate,'yyyy.mm.dd') aa from dual;</p>
<p>&nbsp;</p>
<p>aa</p>
<p>2004.05.09</p>
<p>&nbsp;</p>
<p>SQL&gt; select last_day(sysdate) from dual;</p>
<p>&nbsp;</p>
<p>LAST_DAY(S</p>
<p>31-5月 -04</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p>LOCALTIMESTAMP</p>
<p>语法：LOCALTIMESTAMP</p>
<p>功能：9i新增函数，返回当前会话时区的日期时间。</p>
<p>&nbsp;</p>
<p>Select LOCALTIMESTAMP from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>MONTHS_BETWEEN</strong></p>
<p>语法:MONTHS_BETWEEN(date1,date2)</p>
<p>功能:计算date1和date2之间相差的月数.如果date1&lt;date2，则返回负数；如果date1,date2这两个日期中日分量信息是相同的,或者这两个日期都分别是所在月的最后一天,那么返回的结果是一个整数,否则包括一个小数,小数为富余天数除以31，Oracle以每月31天为准计算结果。</p>
<p>SQL&gt; select months_between('19-12月-1999','19-3月-1999') mon_between from dual;</p>
<p>MON_BETWEEN</p>
<p>&nbsp; 9</p>
<p>&nbsp;</p>
<p>SQL&gt;selectmonths_between(to_date('2000.05.20','yyyy.mm.dd'),to_date('2005.05.20','yyyy.dd')) mon_betw from dual;</p>
<p>MON_BETW</p>
<p>-60</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>NEW_TIME</strong></p>
<p>语法:NEW_TIME(d,zone1,zone2)</p>
<p>功能:计算当时区zone1中的日期和时间是d时候,返回时区zone2中的日期和时间. zone1和zone2是字符串. 给出在this时区=other时区的日期和时间。</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>&nbsp;</p>
<p>NEW_TIME&nbsp;&nbsp; (d,&nbsp;&nbsp; ‘tz1’,&nbsp;&nbsp; ‘tz2’)</p>
<p>&nbsp;</p>
<p>d:：一个有效的日期型变量</p>
<p>tz1&nbsp;&nbsp; &amp;&nbsp;&nbsp; tz2:：下表中的任一时区</p>
<p>&nbsp;</p>
<p>时区1&nbsp;&nbsp; 时区2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 说明</p>
<p>AST&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ADT&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 大西洋标准时间</p>
<p>BST&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; BDT&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 白令海标准时间</p>
<p>CST&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; CDT&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 中部标准时间</p>
<p>EST&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; EDT&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 东部标准时间</p>
<p>GMT&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 格林尼治标准时间</p>
<p>HST&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; HDT&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 阿拉斯加—夏威夷标准时间</p>
<p>MST&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; MDT&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;山区标准时间</p>
<p>NST&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 纽芬兰标准时间</p>
<p>PST&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; PDT&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 太平洋标准时间</p>
<p>YST&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; YDT&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; YUKON标准时间</p>
<p>&nbsp;</p>
<p>SQL&gt; select to_char(sysdate,'yyyy.mm.dd hh24:mi:ss') bj_time,to_char(new_time</p>
<p>2&nbsp; (sysdate,'PDT','GMT'),'yyyy.mm.dd hh24:mi:ss') los_angles from dual;</p>
<p>&nbsp;</p>
<p>BJ_TIME&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; LOS_ANGLES</p>
<p>2004.05.09 11:05:32 2004.05.09 18:05:32</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>NEXT_DAY</strong></p>
<p>语法:NEXT_DAY(d,string)</p>
<p>功能: 给出日期d和星期string之后计算下一个星期的日期. String是星期几;当前会话的语言指定了一周中的某一天.返回值的时间分量与d的时间分量是相同的. String的内容可以忽略大小写.</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>NEXT_DAY(date,'day')</p>
<p>&nbsp;</p>
<p>SQL&gt; select next_day('18-5月-2001','星期五') next_day from dual;</p>
<p>&nbsp;</p>
<p>NEXT_DAY</p>
<p>25-5月 -01</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>NUMTODSINTERNAL</strong></p>
<p>语法：NUMTODSINTERNAL(n,char_expr)</p>
<p>功能：将数字n转换为INTERNAL DAY TO SECOND格式， char_expr可以是DAY\HOUR\MINUTE或SECOND。</p>
<p>&nbsp;</p>
<p>Select NUMTODSINTERNAL(1000,’minute’) from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>NUMTOYMINTERNAL</strong></p>
<p>语法：NUMTOYMINTERNAL(n,char_expr)</p>
<p>功能：将数字n转换为INTERVAL YEAR TO MONTH格式，char_expr可以是year或者month。</p>
<p>&nbsp;</p>
<p>Select NUMTOYMINTERNAL(100,’MONTH’) from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>ROUND</strong></p>
<p>语法:ROUND(d[,format])</p>
<p>功能:将日期d按照由format指定的格式进行四舍五入处理处理.如果没有给format则使用缺省设置`DD`.</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>&nbsp;</p>
<p>Select round(sysdate,’MONTH’) from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>SYS_EXTRACT_UTC</strong></p>
<p>语法：SYS_EXTRACT_UTC(date)</p>
<p>功能：返回特定时区时间所对应的格林威治时间。</p>
<p>&nbsp;</p>
<p>Select SYS_EXTRACT_UTC(systimestamp) from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>SYSDATE</strong></p>
<p>语法: SYSDATE</p>
<p>功能:取得当前的日期和时间,类型是DATE.它没有参数.但在分布式SQL语句中使用时,SYSDATE返回本地数据库的日期和时间.</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>SQL&gt; select to_char(sysdate,'yyyy-mm-dd hh24:mi:ss') from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>SYSTIMESTAMP</strong></p>
<p>语法：SYSTIMESTAMP</p>
<p>功能：9i新增函数，返回当前系统的日期时间及时区。</p>
<p>&nbsp;</p>
<p>Select systimestamp from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TO_DSINTERNAL</strong></p>
<p>语法：TO_DSINTERNAL(char[,’nls_param’])</p>
<p>功能：9i新增函数，将符合特定日期和时间格式的字符串转变为INTERVAL DAY TO SECOND类型。</p>
<p>&nbsp;</p>
<p>Select TO_DSINTERNAL(’58:10:10’) from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TO_TIMESTAMP</strong></p>
<p>语法：TO_TIMESTAMP(char[fmt[,’nls_param’]])</p>
<p>功能：9i新增函数，将符合特定日期和时间格式的字符串转变为TIMESTAMP类型。</p>
<p>select systimestamp from dual</p>
<p>&nbsp;</p>
<p>1. 字符型转成timestamp</p>
<p>Select TO_TIMESTAMP(’01-1月-03’) from dual;</p>
<p>select to_timestamp('01-10月-08 07.46.41.000000000 上午','dd-MON-yy hh:mi:ss.ff AM')&nbsp;</p>
<p>from dual;</p>
<p>&nbsp;</p>
<p>2. timestamp转成date型</p>
<p>select cast(TO_TIMESTAMP('2015-10-01 21:11:11.328', 'yyyy-mm-dd hh24:mi:ss.ff') as date)</p>
<p>from dual;</p>
<p>&nbsp;</p>
<p>3. date型转成timestamp</p>
<p>select cast(sysdate as timestamp) date_to_timestamp</p>
<p>from dual;</p>
<p>&nbsp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TO_TIMESTAMP_TZ</strong></p>
<p>语法：TO_TIMESTAMP_TZ(char[fmt[,’nls_param’]])</p>
<p>功能：9i新增函数，将符合特定日期和时间格式的字符串转变为TIMESTAMP WITH TIME ZONE类型。</p>
<p>&nbsp;</p>
<p>Select TO_TIMESTAMP_TZ(’20130101’,’yyyymmdd’) from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TO_YMINTERNAL</strong></p>
<p>语法：TO_YMINTERNAL(char)</p>
<p>功能：9i新增函数，将符合特定日期和时间格式的字符串转变为INTERVAL YEAR TO MONTH类型。</p>
<p>&nbsp;</p>
<p>select TO_TIMESTAMP('2015-10-01 21:11:11.328', 'yyyy-mm-dd hh24:mi:ss.ff') -</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; TO_TIMESTAMP('2015-10-01 11:11:11.328', 'yyyy-mm-dd hh24:mi:ss.ff')</p>
<p>&nbsp; from dual;</p>
<p>&nbsp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TRUNC</strong></p>
<p>语法:TRUNC(d,format)</p>
<p>功能:截断日期时间数据，计算截尾到由format指定单位的日期d.缺省参数同ROUNG.</p>
<p>使用位置:过程性语言和SQL语句。如果fmt='mi'表示保留分,截断秒，如此类推。</p>
<p>&nbsp;</p>
<p>SQL&gt; select to_char(trunc(sysdate,'hh'),'yyyy.mm.dd hh24:mi:ss') hh,</p>
<p>&nbsp; 2&nbsp; to_char(trunc(sysdate,'mi'),'yyyy.mm.dd hh24:mi:ss') hhmm from dual;</p>
<p>&nbsp;</p>
<p>HH&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; HHMM</p>
<p>2004.05.09 11:00:00 2004.05.09 11:17:00</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TZ_OFFSET</strong></p>
<p>语法：TO_OFFSET(time_zone_name||sessiontimezone||dbtimezone)</p>
<p>功能：9i新增函数，返回特定时区与UTC相比的时区偏移。</p>
<p>&nbsp;</p>
<p>Select TO_OFFSET (’EST’) from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p align="center"><strong>F.5&nbsp;&nbsp; </strong><strong>转换函数</strong></p>
<p>(asciistr,bin_to_num,cast,chartorowid,compose,convert,decompose,hextoraw, INTERVAL,rawtonhex,rowidtochar,rowidtonchar,scn_to_timestamp,timestamp_to_scn,to_char,to_clob,to_date,to_lob,to_label,to_multi_byte,to_nchar,to_number,to_single_byte,translate...using,unistr)</p>
<p>&nbsp;</p>
<p>说明：用于将数值从一种数据类型转换为另一种数据类型。</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><strong>ASCIISTR</strong></p>
<p>语法：ASCIISTR(s)</p>
<p>功能：9i新增函数，将任意字符集的字符串转变为数据库字符集的ASCII字符串。</p>
<p>&nbsp;</p>
<p>Select ASCIISTR (’中国’) 中 from dual;</p>
<p>&nbsp;</p>
<p>中</p>
<p>\4E2D\56FD</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>BIN_TO_NUM</strong></p>
<p>语法：BIN_TO_NUM(expr[,expr]…)</p>
<p>功能：9i新增函数，用于将位向量值转变为实际的数字值。</p>
<p>&nbsp;</p>
<p>Select BIN_TO_NUM(1,0,1,1,1) 中 from dual;</p>
<p>&nbsp;</p>
<p>中</p>
<p>23</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>CAST</strong></p>
<p>语法：CAST(expr AS type_name)</p>
<p>功能：用于将一个内置数据类型或集合类型转变为另一个内置数据类型或集合类型。可以作用于长度为0的空字段视图建表格之用。</p>
<p>&nbsp;</p>
<p>Select cast(SYSDATE AS VARCHAR2) 中 from dual;</p>
<p>Create table tb_dual nologging as Select cast(null as varchar2(1)) from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>CHARTOROWID</strong></p>
<p>语法:CHARTOROWID(string)</p>
<p>功能: 将字符数据类型转换为ROWID类型,把包含外部格式的ROWID的CHAR或VARCHAR2数值转换为内部的二进制格式.参数string必须是包含外部格式的ROWID的18字符的字符串.oracle7和oracle8中的外部格式是不同的.CHARTOROWID是ROWIDTOCHAR的反函数.</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>&nbsp;</p>
<p>SQL&gt; select rowid,rowidtochar(rowid),ename from scott.emp;</p>
<p>&nbsp;</p>
<p>ROWID&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ROWIDTOCHAR(ROWID) ENAME</p>
<p>AAAAfKAACAAAAEqAAA AAAAfKAACAAAAEqAAA SMITH</p>
<p>AAAAfKAACAAAAEqAAB AAAAfKAACAAAAEqAAB ALLEN</p>
<p>AAAAfKAACAAAAEqAAC AAAAfKAACAAAAEqAAC WARD</p>
<p>AAAAfKAACAAAAEqAAD AAAAfKAACAAAAEqAAD JONES</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>COMPOSE</strong></p>
<p>语法：COMPOSE(string)</p>
<p>功能：9i新增函数，用于将输入字符串转变为UNICODE字符串值。</p>
<p>&nbsp;</p>
<p>Select COMPOSE(‘o’||unistr(‘\0308’)) 中 from dual;</p>
<p>&nbsp;</p>
<p>中</p>
<p>?</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>CONVERT</strong></p>
<p>语法:CONVERT(string,dest_set[,source_set])</p>
<p>功能:将字符串string从source_set所表示的字符集转换为由dest_set所表示的字符集.如果source_set没有被指定,它缺省的被设置为数据库的字符集.</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>&nbsp;</p>
<p>SQL&gt; select convert('中国','US7ASCII','WE8ISO8859P1') "conversion" from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>DECOMPOSE</strong></p>
<p>语法：DECOMPOSE(string)</p>
<p>功能：9i新增函数，用于分解字符串并返回相应的UNICODE字符串。</p>
<p>&nbsp;</p>
<p>Select COMPOSE(‘chateoux’) 中 from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>HEXTORAW</strong></p>
<p>语法:HEXTORAW(string)</p>
<p>功能: 将string一个十六进制构成的字符串转换为二进制RAW数值. String中的每两个字符表示了结果RAW中的一个字节..HEXTORAW和RAWTOHEX为相反的两个函数.</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>&nbsp;</p>
<p>Select HEXTORAW (‘AB56’) 中 from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>INTERVAL</strong></p>
<p>语法：INTERVAL 'integer [- integer]' {YEAR | MONTH} [(precision)][TO {YEAR | MONTH}]</p>
<p>功能：该数据类型常用来表示一段时间差, 注意时间差只精确到年和月. precision为年或月的精确域, 有效范围是0到9, 默认值为2。</p>
<p>&nbsp;</p>
<p>INTERVAL '123-2' YEAR(3) TO MONTH</p>
<p>表示: 123年2个月, "YEAR(3)" 表示年的精度为3, 可见"123"刚好为3为有效数值, 如果该处YEAR(n), n&lt;3就会出错, 注意默认是2.</p>
<p>&nbsp;</p>
<p>INTERVAL '11:12:10.1234567' HOUR TO SECOND</p>
<p>表示：小时，秒</p>
<p>结果：+00 11:12:10.123457</p>
<p>&nbsp;</p>
<p>INTERVAL '123' YEAR(3)</p>
<p>表示: 123年0个月</p>
<p>&nbsp;</p>
<p>INTERVAL '300' MONTH(3)</p>
<p>表示: 300个月, 注意该处MONTH的精度是3啊.</p>
<p>&nbsp;</p>
<p>INTERVAL '4' YEAR</p>
<p>表示: 4年, 同 INTERVAL '4-0' YEAR TO MONTH 是一样的</p>
<p>&nbsp;</p>
<p>INTERVAL '50' MONTH</p>
<p>表示: 50个月, 同 INTERVAL '4-2' YEAR TO MONTH 是一样</p>
<p>&nbsp;</p>
<p>INTERVAL '123' YEAR</p>
<p>表示: 该处表示有错误, 123精度是3了, 但系统默认是2, 所以该处应该写成 INTERVAL '123' YEAR(3) 或"3"改成大于3小于等于9的数值都可以的</p>
<p>&nbsp;</p>
<p>INTERVAL '5-3' YEAR TO MONTH + INTERVAL '20' MONTH =</p>
<p>INTERVAL '6-11' YEAR TO MONTH</p>
<p>表示: 5年3个月 + 20个月 = 6年11个月</p>
<p>&nbsp;</p>
<p><strong>RAWTONHEX</strong></p>
<p>语法:RAWTONHEX(rawvalue)</p>
<p>功能:9i新增函数，将RAW类数值rawvalue转换为一个相应的十六进制表示的字符串. rawvalue中的每个字节都被转换为一个双字节的字符串. RAWTOHEX和HEXTORAW是两个相反的函数.</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>&nbsp;</p>
<p>Select rawtonhex(‘7D’) from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>ROWIDTOCHAR</strong></p>
<p>语法:ROWIDTOCHAR(rowid)</p>
<p>功能:9i新增函数，将ROWID类型的数值rowid转换为varchar2的字符串表示,在oracle7和oracle8之间有些不一样的地方. ROWIDTOCHAR和CHARTOROWID是两个相反的函数.</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>&nbsp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>ROWIDTONCHAR</strong></p>
<p>语法:ROWIDTOCHAR(rowid)</p>
<p>功能:9i新增函数，将ROWID类型的数值rowid转换为Nvarchar2的字符串表示,在oracle7和oracle8之间有些不一样的地方. ROWIDTOCHAR和CHARTOROWID是两个相反的函数.</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>&nbsp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>SCN_TO_TIMESTAMP</strong></p>
<p>语法:SCN_TO_TIMESTAMP(number)</p>
<p>功能:10g新增函数，根据输入的scn值返回对应的大概日期时间，其中number用于指定scn值.</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>&nbsp;</p>
<p>Select SCN_TO_TIMESTAMP(ora_rowscn) from emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TIMESTAMP_TO_SCN</strong></p>
<p>语法:TIMESTAMP_TO_SCN(timestamp)</p>
<p>功能:10g新增函数，用于根据输入的timestamp返回所对应的scn值，其中timestamp、用于指定日期时间。</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>&nbsp;</p>
<p>Select TIMESTAMP_TO_SCN(order_date) from emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TO_CHAR</strong></p>
<p>语法1:TO_CHAR(character)</p>
<p>功能1:用于将NCHAR,NVARCHAR2,CLOB,NCLOB数据转变为数据库字符集数据，当用于NCHAR,NVARCHAR2,NCLOB时字符用单引号括起来，前面加上n。</p>
<p>&nbsp;</p>
<p>Select to_char（n’中国’） from dual;</p>
<p>&nbsp;</p>
<p>语法2:TO_CHAR(d [,format[,nlsparams]])</p>
<p>功能2:将日期d转换为一个VARCHAR2类型的字符串.format指定日期格式,.如果没有给定format,使用的就是该会话的缺省日期格式.nlsparams指定NLS参数. nlsparams的格式是:“NLS_DATE_LANGUAGE”</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>&nbsp;</p>
<p>select to_char(sysdate,'yyyy/mm/dd hh24:mi:ss') from dual;</p>
<p>2004/05/09 21:14:41</p>
<p>&nbsp;</p>
<p>语法3:TO_CHAR(labels[,format])</p>
<p>功能3:将MISLABEL的LABEL转换为一个VARCHAR2类型的变量.</p>
<p>使用位置:在trusted数据库的过程性语句和SQL语句。</p>
<p>&nbsp;</p>
<p>语法4: TO_CHAR(num[,format[,nlsparams]])</p>
<p>功能4:将NUMBER类型的参数num转换为一个VARCHAR2类型的变量.如果指定了format,那么它会控制这个转换处理.表5-5列除了可以使用的数字格式.如果没有指定format,它会控制这个转换过程.下面列出了可以使用的数字格式.如果没有指定format,那么结果字符串将包含和num中有效位的个数相同的字符. nlsparams用来指定小数点和千分位分隔符和货币符号.可以使用的格式:`NLS_NUMERIC_CHARS=”dg”NLS_CURRENCY=”string”</p>
<p>d和g分别表示列小数点和千分位分隔符. String表示了货币的符号.例如,在美国小数点分隔符通常是一个句点(.),分组分隔符通常是一个逗号(,),而千分位符号通常是一个$.</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>&nbsp;</p>
<p>SELECT TO_CHAR(TO_DATE('11-oct-2007'), 'fmDdthsp "of" Month, Year') FROM DUAL;</p>
<p>以上正确，需要注意的是不属于转换日期格式标识符需要使用双引号，如上面的"of"</p>
<p>&nbsp;</p>
<p>SELECT promo_name, TRIM(TO_CHAR(promo_end_date,'Day')) ||', '||</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; TRIM(TO_CHAR(promo_end_date,'Month')) ||' '||</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; TRIM(TO_CHAR(promo_end_date,'DD, YYYY')) AS last_day</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; FROM promotions;</p>
<p>等价于下面，fm有trim的作用去掉多余空格</p>
<p>SELECT promo_name,TO_CHAR(promo_end_date,'fmDay')||','||</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; TO_CHAR(promo_end_date,'fmMonth')||' '||</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; TO_CHAR(promo_end_date,'fmDD, YYYY') AS last_day</p>
<p>&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;FROM promotions;</p>
<p>上述当中，Day\DAY\day等等转换后都是带空格的，而YYYY则不会。</p>
<p>&nbsp;</p>
<p>--将number格式转换为货币格式，前面均带空格</p>
<p>select TO_CHAR(12345,'$99999D99') from dual;-- $12345.00</p>
<p>SELECT TO_CHAR(1890.55,'$00G000D00') FROM DUAL;-- $01,890.55</p>
<p>SELECT TO_CHAR(1890.55,'$99G999D99') FROM DUAL;--&nbsp;&nbsp; $1,890.55</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TO_CLOB</strong></p>
<p>语法:TO_CLOB (char)</p>
<p>功能:9i新增函数，将字符串转变为CLOB类型。Char参数使用NCHAR,NVARCHAR2，NCLOB类型，字符串需要单引号括起来，且在前面加上n.</p>
<p>&nbsp;</p>
<p>Select TO_CLOB（n’中国’） from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TO_DATE</strong></p>
<p>语法:TO_DATE(String[,format[,nlsparams]])</p>
<p>功能:将符合特定日期格式的字符串转变为date类型. format是一个日期格式字符串.当不指定format的时候,使用该会话的缺省日期格式，需要特别注意的，缺省格式并不适用'2015-03-03'这种形式。</p>
<p>&nbsp;</p>
<p>Select to_date(‘20130101’,’yyyymmdd’) from dual;--正确</p>
<p>SELECT TO_DATE('01/JANUARY/2007') FROM DUAL;--正确，缺省支持</p>
<p>SELECT TO_DATE('01-JANUARY-2007') FROM DUAL;--正确，缺省支持</p>
<p>SELECT TO_DATE('2015-03-03') FROM DUAL;--错误，缺省不支持</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TO_LOB</strong></p>
<p>语法:TO_LOB (long_column)</p>
<p>功能:9i新增函数，将LONG或LONG ROW列的数据转变为相应的LOB类型。但需要注意的是，在单纯的select语句中会报错，如例子所示。</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>&nbsp;</p>
<p>例子：to_lob转化long</p>
<p align="left">select VIEW_NAME,to_lob(text) text from user_views;&nbsp; --会报错</p>
<p align="left">create table temp_liutao nologging as select VIEW_NAME,to_lob(text) text from user_views&nbsp; --通过</p>
<p>&nbsp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TO_LABEL</strong></p>
<p>语法:TO_LABEL(String[,format])</p>
<p>功能:将String转换为一个MLSLABEL类型的变量. String可以是VARCHAR2或者CHAR类型的参数.如果指定了format,那么它就会被用在转换中.如果没有指定format,那么使用缺省的转换格式.</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TO_MULTI_BYTE</strong></p>
<p>语法:TO_MULTI_BYTE(String)</p>
<p>功能:计算所有单字节字符都替位换位等价的多字节字符的String.该函数只有当数据库字符集同时包含多字节和单字节的字符的时候有效.否则, String不会进行任何处理. TO_MULTI_BYTE和TO_SINGLE_BYTE是相反的两个函数.</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>&nbsp;</p>
<p>SQL&gt;&nbsp; select to_multi_byte('高') from dual;</p>
<p>&nbsp;</p>
<p>TO</p>
<p>高</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TO_NCHAR</strong></p>
<p>语法1:TO_NCHAR(char)</p>
<p>功能1:将字符串由数据库字符集转变为民族字符集。</p>
<p>&nbsp;</p>
<p>SQL&gt;&nbsp; select TO_NCHAR ('高') from dual;</p>
<p>&nbsp;</p>
<p>语法2:TO_NCHAR(date,[,fmt[,nls_param]])</p>
<p>功能2:将日期时间值转变为民族字符集。</p>
<p>&nbsp;</p>
<p>SQL&gt;&nbsp; select TO_NCHAR (sysdate) from dual;</p>
<p>&nbsp;</p>
<p>语法3:TO_NCHAR(number)</p>
<p>功能3:将数字值转变为民族字符集。</p>
<p>&nbsp;</p>
<p>SQL&gt;&nbsp; select TO_NCHAR (10) from dual;</p>
<p>&nbsp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TO_NUMBER</strong></p>
<p>语法: TO_NUMBER(String[,format[,nlsparams]])</p>
<p>功能:将CHAR或者VARCHAR2类型的String转换为一个NUMBER类型的数值.如果指定了format,那么String应该遵循相应的数字格式. Nlsparams的行为方式和TO_CHAR中的完全相同.TO_NUMBER和TO_CHAR是两个相反的函数.</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>&nbsp;</p>
<p>SQL&gt; select to_number('1999') year from dual;</p>
<p>&nbsp;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp; YEAR</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp; 1999</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TO_SINGLE_BYTE</strong></p>
<p>语法: TO_SINGLE_BYTE(String )</p>
<p>功能:计算String中所有多字节字符都替换为等价的单字节字符.该函数只有当数据库字符集同时包含多字节和单字节的字符的时候有效.否则, String不会进行任何处理.</p>
<p>TO_MULTI_BYTE和TO_SINGLE_BYTE是相反的两个函数.</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>&nbsp;</p>
<p>Select TO_SINGLE_BYTE(‘a b c’) from dual;</p>
<p>&nbsp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>TRANSLATE…USING</strong></p>
<p>语法: TRANSLATE(str1 USING zfj)</p>
<p>功能:将字符串转变为数据库字符集(char_cs)或民族字符集(nchar_cs)</p>
<p>&nbsp;</p>
<p>Select TRANSLATE(‘中国’ using nchar_cs) from dual;</p>
<p>&nbsp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>UNISTR</strong></p>
<p>语法: UNISTR(str1)</p>
<p>功能:9i新增函数，输入字符串返回相应的UNICODE字符</p>
<p>&nbsp;</p>
<p>Select UNISTR (‘\00D6’) from dual;</p>
<p>&nbsp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p align="center"><strong>F.6&nbsp; </strong><strong>分组统计函数</strong></p>
<p>&nbsp;</p>
<p>(avg,corr,count,covar_pop,covar_samp,cume_dist,dense_rank,first,group_id,grouping,grouping_id,glb,last,listagg,lub,max,min,percent_rank,percentile_cont,percentile_disc,rank,stddev,stddev_pop,stddev_samp,sum,var_pop,var_samp,variance)</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>说明：分组函数也被称为多行函数，它会根据输入的多行数据返回一个结果。主要用于执行数据统计或汇总操作，并且分组函数只能出现在select语句选择列表、order by子句和having子句中。注意分组函数不能直接在plsql中引用，只能在内嵌select语句中使用。</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><strong>AVG</strong></p>
<p>语法:AVG([DISTINCT|ALL]col)</p>
<p>功能:返回一列数据的平均值,缺省使用是ALL修饰符，all表示对所有的值求平均值,distinct排重后再求平均值</p>
<p>使用位置:查询列表和GROUP BY子句.</p>
<p>&nbsp;</p>
<p>SQL&gt; select avg(distinct sal) from gao.table3;</p>
<p>&nbsp;</p>
<p>AVG(DISTINCTSAL)</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3333.33</p>
<p>&nbsp;</p>
<p>SQL&gt; select avg(all sal) from gao.table3;</p>
<p>&nbsp;</p>
<p>AVG(ALLSAL)</p>
<p>&nbsp;&nbsp;&nbsp; 2592.59</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>CORR</strong></p>
<p>语法:CORR([expr1,expr2)</p>
<p>功能:返回成对数值的相关系数，其数值使用表达式”covar_pop(expr1,expr2)/(stddev_pop(expr1)*stddev_pop(expr2))”</p>
<p>使用位置:查询列表和GROUP BY子句.</p>
<p>&nbsp;</p>
<p>SQL&gt; select corr(list_,min_) from gao.table3;</p>
<p>&nbsp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>COUNT</strong></p>
<p>语法:COUNT(*|[DISTINCT|ALL] col)</p>
<p>功能:得到查询中行的数目.如果使用了*获得行的总数.如果在参数中传递的是选择列表,那么计算的是非空数值。我基于10G测试，有主键情况下，count(主键)最快，count(1)和count(*)调动主键统计，时间上一样；无主键情况下count(索引列)最快，但需要注意count(列名)统计不包括null，count(常量)和count(*)包括null</p>
<p>&nbsp;</p>
<p>Select count(distinct sal) from emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>COVAR_POP</strong></p>
<p>语法:COVAR_POP(expr1,expr2)</p>
<p>功能:返回成对数字的协方差，其数值使用表达式”(sum(expr1*expr2)-sum(expr1)*sum(expr2)/n)/n”</p>
<p>&nbsp;</p>
<p>Select COVAR_POP(column1,column2) from emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>COVAR_SAMP</strong></p>
<p>语法:COVAR_SAMP(expr1,expr2)</p>
<p>功能:返回成对数字的协方差，其数值使用表达式”(sum(expr1*expr2)-sum(expr1)*sum(expr2)/n)/n-1”</p>
<p>&nbsp;</p>
<p>Select COVAR_SAMP(column1,column2) from emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>CUME_DIST</strong></p>
<p>语法:CUME_DIST(expr1,expr2…) within group (order by expr1,expr2…)</p>
<p>功能:返回特定数值在一组行数据中的累积分布比例。</p>
<p>&nbsp;</p>
<p>Select CUME_DIST(2000) within group (order by sel) from emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>DENSE_RANK</strong></p>
<p>语法:DENSE_RANK(expr1,expr2…) within group (order by expr1,expr2…)</p>
<p>功能:返回特定数据在一组行数据中的等级。</p>
<p>&nbsp;</p>
<p>Select DENSE_RANK (5000) within group (order by sel) from emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>FIRST</strong></p>
<p>语法:FIRST</p>
<p>功能:9i新增，不能单独使用，必须与其他分组函数结合使用。通过使用该函数，可以取得排序等级的第一级，然后然后使用分组函数汇总该等级的数据。</p>
<p>&nbsp;</p>
<p>Select min(sal) keep (dense_rank first order by comm desc) from emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>GROUP_ID</strong></p>
<p>语法:GROUP_ID</p>
<p>功能:9i新增，用于区分分组结果中的重复行。</p>
<p>&nbsp;</p>
<p>Select deptno,job,avg(sal),group_id() from emp group by deptno,rollup(deptno,job);</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>GROUPING</strong></p>
<p>语法：GROUPING(expr)</p>
<p>功能:用于确定统计结果是否使用了特定的表达式，返回0则用到了表达式，1则未用。</p>
<p>例如:select corp_code,org_level,count(1),</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; grouping(corp_code),</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; grouping(org_level)</p>
<p>&nbsp; from tb_sys_organization</p>
<p>group by rollup(corp_code, org_level);</p>
<p>&nbsp;</p>
<p>select case grouping(corp_code)</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; when 1 then 'all_corp' else corp_code end corp_code,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; case grouping(org_level)</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; when 1 then 'all_org' else org_level end org_level,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; count(1)</p>
<p>&nbsp; from tb_sys_organization</p>
<p>group by rollup(corp_code, org_level);</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>GROUPING_ID</strong></p>
<p>语法:GROUPING_ID(expr1[,expr2]…)</p>
<p>功能:9i新增，用于返回对应于特定行的grouping位向量的值。</p>
<p>&nbsp;</p>
<p>Select deptno,job,sum(sal),grouping_id(job,deptno) from emp group by rollup(deptno,jon)</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>GLB</strong></p>
<p>语法:GLB ([DISTINCT|ALL]label)</p>
<p>功能:获得由label界定的最大下界.函数仅用于trusted oracle.</p>
<p>使用位置:trusted数据库的选择列表和GROUP BY子句.</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>LAST</strong></p>
<p>语法:LAST</p>
<p>功能:9i新增，不能单独使用，必须与其他分组函数结合使用。通过使用该函数，可以取得排序等级的最后一级，然后使用分组函数汇总该等级的数据。</p>
<p>&nbsp;</p>
<p>Select min(sal) keep (dense_rank last order by comm) from emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>LISTAGG</strong></p>
<p>语法:listagg</p>
<p>功能:列转行</p>
<p>select listagg(o.rybs, ';') within group(order by o.rybs)</p>
<p>&nbsp; from gk_xszrr o</p>
<p>&nbsp;where rownum &lt;= 100;</p>
<p>----------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>LUB</strong></p>
<p>语法:LUB ([DISTINCT|ALL]label)</p>
<p>功能:获得由label界定的最小上界.用于trusted oracle.数据库.</p>
<p>使用位置:trusted数据库的选择列表和GROUP BY子句.过程性语言和SQL语句。</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>MAX</strong></p>
<p>语法:MAX([DISTINCT|ALL]col)</p>
<p>功能:获得选择列表或表达式的最大值，ALL表示对所有的值求最大值,DISTINCT表示对不同的值求最大值,相同的只取一次</p>
<p>使用位置:仅用于查询选择和GROUP BY子句.</p>
<p>&nbsp;</p>
<p>SQL&gt; select max(distinct sal) from scott.emp;</p>
<p>&nbsp;</p>
<p>MAX(DISTINCTSAL)</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 5000</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>MIN</strong></p>
<p>语法:MIN([DISTINCT|ALL]col)</p>
<p>功能:获得选择列表或表达式的最小值，ALL表示对所有的值求最小值,DISTINCT表示对不同的值求最小值,相同的只取一次</p>
<p>使用位置:仅用于查询选择和GROUP BY子句.</p>
<p>&nbsp;</p>
<p>SQL&gt; select min(all sal) from gao.table3;</p>
<p>&nbsp;</p>
<p>MIN(ALLSAL)</p>
<p>&nbsp;&nbsp;&nbsp; 1111.11</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>PERCENT_RANK</strong></p>
<p>语法:PERCENT_RANK(expr1,expr2…)WITHIN GROUP (ORDER BY expr1,expr2…)</p>
<p>功能:该函数用于返回特定数值在统计级别中所占的比例。</p>
<p>&nbsp;</p>
<p>SQL&gt; select percent_rank(3000) within group(order by sal) from emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>PERCENTILE_CONT</strong></p>
<p>语法:PERCENTILE_CONT(percent_expr)WITHIN GROUP (ORDER BY expr)</p>
<p>功能:9i新增，用于返回在统计级别中处于某个百分点的特定数值（按照连续分布模型确定）。</p>
<p>&nbsp;</p>
<p>SQL&gt; select percentile_cont(.6) within group(order by sal) from emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>PERCENTILE_DISC</strong></p>
<p>语法:PERCENTILE_DISC(percent_expr)WITHIN GROUP (ORDER BY expr)</p>
<p>功能:9i新增，用于返回在统计级别中处于某个百分点的特定数值（按照离散分布模型确定）。</p>
<p>&nbsp;</p>
<p>SQL&gt; select percentile_cont(.6) within group(order by sal) from emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>RANK</strong></p>
<p>语法:RANK(expr1,expr2…)WITHIN GROUP (ORDER BY expr1,expr2…)</p>
<p>功能:该函数用于返回特定数值中所占据的等级。</p>
<p>&nbsp;</p>
<p>SQL&gt; select rank(3000) within group(order by sal) from emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>STDDEV</strong></p>
<p>语法:STDDEV([DISTINCT|ALL]col)</p>
<p>功能:获得选择列表的标准差.标准差为方差(VARIANCE)的平方根, ALL表示对所有的值求标准差,DISTINCT表示只对不同的值求标准差.</p>
<p>使用位置:仅用于查询选择和GROUP BY子句.</p>
<p>SQL&gt; select stddev(sal) from scott.emp;</p>
<p>&nbsp;</p>
<p>STDDEV(SAL)</p>
<p>&nbsp; 1182.5032</p>
<p>&nbsp;</p>
<p>SQL&gt; select stddev(distinct sal) from scott.emp;</p>
<p>&nbsp;</p>
<p>STDDEV(DISTINCTSAL)</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1229.951</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>STDDEV_POP</strong></p>
<p>语法:STDDEV_POP(col)</p>
<p>功能:返回统计标准差，其数值是统计方差的平方根.</p>
<p>使用位置:仅用于查询选择和GROUP BY子句.</p>
<p>SQL&gt; select stddev_pop(sal) from scott.emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>STDDEV_SAMP</strong></p>
<p>语法:STDDEV_SAMP(col)</p>
<p>功能:返回采样标准差，其数值是采样方差的平方根.</p>
<p>SQL&gt; select stddev_samp(sal) from scott.emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>SUM</strong></p>
<p>语法:SUM([DISTINCT|ALL]col)</p>
<p>功能:返回选择的数值和总和</p>
<p>使用位置:仅用于查询选择和GROUP BY子句.</p>
<p>Select sum(sal) from emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>VAR_POP</strong></p>
<p>语法:VAR_POP([DISTINCT|ALL]col)</p>
<p>功能:返回统计方差.使用公式为(sum(expr*expr)-sum(expr)*sum(expr)/count(expr))/(count(expr)</p>
<p>使用位置:仅用于查询选择和GROUP BY子句.</p>
<p>SQL&gt; select VAR_POP (sal) from scott.emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>VAR_SAMP</strong></p>
<p>语法:VAR_SAMP([col)</p>
<p>功能:返回采样方差.使用公式为(sum(expr*expr)-sum(expr)*sum(expr)/count(expr))/(count(expr-1)</p>
<p>使用位置:仅用于查询选择和GROUP BY子句.</p>
<p>SQL&gt; select variance(sal) from scott.emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>VARIANCE</strong></p>
<p>语法:VARIANCE([DISTINCT|ALL]col)</p>
<p>功能:返回选择列或表达式的采样方差.使用公式为(sum(expr*expr)-sum(expr)*sum(expr)/count(expr))/(count(expr-1)</p>
<p>使用位置:仅用于查询选择和GROUP BY子句.</p>
<p>SQL&gt; select variance(sal) from scott.emp;</p>
<p>&nbsp;</p>
<p>VARIANCE(SAL)</p>
<p>&nbsp;&nbsp;&nbsp; 1398313.9</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p>分组函数，除了count(*)，count(1)，其他分组函数都会忽略null行，包括count(列名)。</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p align="center"><strong>F.7&nbsp; </strong><strong>集合函数</strong></p>
<p>(cardinality,collect,powermultiset,powermultiset_by_cardinality,set)</p>
<p>&nbsp;</p>
<p>说明：10g新增，为了扩展集合类型（嵌套表和VARRAY）的功能，新增的针对集合类型的函数。</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><strong>CARDINALITY</strong></p>
<p>语法:CARDINALITY (nested_table)</p>
<p>功能:10g新增函数，返回嵌套表的实际元素个数。</p>
<p>&nbsp;</p>
<p>SQL&gt; select product_id,CARDINALITY(ad_text) from a;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>COLLECT</strong></p>
<p>语法:COLLECT (column)</p>
<p>功能:10g新增函数，用于根据输入列和被选中行建立嵌套表结果。</p>
<p>&nbsp;</p>
<p>SQL&gt; select cast(COLLECT(ad_text) as t) from a;--t是嵌套表</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>POWERMULTISET</strong></p>
<p>语法:POWERMULTISET(expr)</p>
<p>功能:10g新增函数，用于生成嵌套表的超集（包含所非空的嵌套表）。</p>
<p>&nbsp;</p>
<p>SQL&gt; select cast(POWERMULTISET (ad_text) as t) from a;--t是嵌套表</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>POWERMULTISET_BY_CARDINALITY</strong></p>
<p>语法:POWERMULTISET_BY_CARDINALITY(expr,cardinatility)</p>
<p>功能:10g新增函数，用于根据嵌套表和元素个数，生成嵌套表的超集（包含所非空的嵌套表）。</p>
<p>&nbsp;</p>
<p>SQL&gt; select cast(POWERMULTISET_BY_CARDINALITY(ad_text) as t) from a;--t是嵌套表</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>SET</strong></p>
<p>语法:SET(nested_table)</p>
<p>功能:改函数用于取消嵌套表中的重复结果，并生成新的嵌套表。</p>
<p>&nbsp;</p>
<p>SQL&gt; select SET(nested_table) from a;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p align="center"><strong>F.8&nbsp; </strong><strong>对象函数</strong></p>
<p>&nbsp;</p>
<p>(deref,make_ref,ref,reftohex,value)</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>说明：对象函数用于操纵REF对象。REF对象实际是指对象类型数据的指针。</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><strong>DEREF</strong></p>
<p>语法:DEREF(expr)</p>
<p>功能:该函数用于返回参照对象exp所引用的对象实例。</p>
<p>&nbsp;</p>
<p>SQL&gt; select DEREF(address).city from table_name;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>MAKE_REF</strong></p>
<p>语法:MAKE_REF(object_table|object_view,key)</p>
<p>功能:该函数可以基于对象视图或对象表（存在基于主键的对象标识符）的一行数据建立REF。</p>
<p>&nbsp;</p>
<p>SQL&gt; select MAKE_REF(oc_inventocies,3003) from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>REF</strong></p>
<p>语法:REF(expr)</p>
<p>功能:该函数用于返回对象行所对应的REF值。</p>
<p>&nbsp;</p>
<p>SQL&gt; select REF(e) from table_name e;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>REFTOHEX</strong></p>
<p>语法:REFTOHEX(expr)</p>
<p>功能:该函数用于将REF值转变为十六进制字符串。</p>
<p>&nbsp;</p>
<p>SQL&gt; select REFTOHEX(REF(e)) from table_name e;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>VALUE</strong></p>
<p>语法:VALUE(expr)</p>
<p>功能:该函数用于返回行对象所对应的对象实例数据，其中expr用于指定行对象的别名。</p>
<p>&nbsp;</p>
<p>SQL&gt; select value(e).city from table_name e;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p align="center"><strong>F.9&nbsp; </strong><strong>其他函数</strong></p>
<p>&nbsp;</p>
<p>(bfilename,coalesce,decode,depth,dump,empty_clob/empty_blob,existsnode,extract,extractvalue,greatest,greatest_lb,least,least_ub,nls_charset_decl_len,nls_charser_id,nls_charser_name,nullif,nvl2,over,path,sys_connect_by_path,sys_context,sys_dburigen,sys_guid,sys_typeid,sys_xmlagg,sys_xmlgen,uid,updatexml,user,userenv,vsize,xmlagg,xmlcolatival,xmlconcat,xmlelement,xmlforest,xmlsequence,xmltransform)</p>
<p>&nbsp;</p>
<p>说明：除了上述涉及的函数外，Oracle还提供了一些单行函数。</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><strong>BFILENAME</strong></p>
<p>语法: BFILENAME(directory,file_name)</p>
<p>功能:获得操作系统中与物理文件file_name相关的BFILE位置指示符. Directory是与OS路径相关的DIRECTORY类型对象，file_name是OS文件的名称。</p>
<p>使用位置:过程性语言和SQL语句。</p>
<p>&nbsp;</p>
<p>SQL&gt;insert into file_tb1 values(bfilename('lob_dir1','image1.gif'));</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>COALESCE</strong></p>
<p>语法:COALESCE(exp1,exp2,exp3,...)</p>
<p>功能:9i新增，依次查找各参数，遇到非NULL则返回，各参数或表达式数据类型必须一致，如果都为null则返回null。</p>
<p>&nbsp;</p>
<p>Select COALESCE(v_e1,v_e2) from a;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>DECODE</strong></p>
<p>语法:DECODE(base_expr,comparel,valuel,Compare2,value2,…default)</p>
<p>功能:把base_expr与后面的每个compare(n)进行比较,如果匹配返回相应的value (n).如果没有发生匹配,则返回default，每个valuel数据类型必须一致，如果没有default则返回null。</p>
<p>&nbsp;</p>
<p>Select decode(a,’金’,1,’银’,2,0) from table_name;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>DEPTH</strong></p>
<p>语法:DEPTH(n)</p>
<p>功能:9i新增，用于返回xml方案under_path路径所对应的相对层数，其中参数n用于指定相对层数。</p>
<p>&nbsp;</p>
<p>Select fath(1),depth(2) from a;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>DUMP</strong></p>
<p>语法:DUMP(expr[,number_format[,start_position][,length]])</p>
<p>功能:获得有关expr的内部表示信息的VARCHAR2类型的数值. number_format指定了按照下面返回数值的基数(base):</p>
<p>number_format &nbsp;&nbsp;&nbsp;结果</p>
<p>8&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 八进制表示</p>
<p>10&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;十进制表示</p>
<p>16&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 十六进制表示</p>
<p>17&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 单字符</p>
<p>默认的值是十进制.</p>
<p>如果指定了start_position和length,那么返回从start_position开始的长为length的字节.缺省返回全部.</p>
<p>数据类型按照下面规定的内部数据类型的编码作为一个数字进行返回.</p>
<p>代码&nbsp;&nbsp;&nbsp; 数据类型</p>
<p>1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; VARCHAR2</p>
<p>2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; NUMBER</p>
<p>8&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; LONG</p>
<p>12&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; DATE</p>
<p>23&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; RAW</p>
<p>69&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ROWID</p>
<p>96&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;CHAR</p>
<p>106&nbsp;&nbsp;&nbsp;&nbsp; MLSLABEL</p>
<p>&nbsp;</p>
<p>SQL&gt; col global_name for a30</p>
<p>SQL&gt; col dump_string for a50</p>
<p>SQL&gt; set lin 200</p>
<p>SQL&gt; select global_name,dump(global_name,1017,8,5) dump_string from global_name;</p>
<p>&nbsp;</p>
<p>GLOBAL_NAME&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; DUMP_STRING</p>
<p>ORACLE.WORLD&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;Typ=1 Len=12 CharacterSet=ZHS16GBK: W,O,R,L,D</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>EMPTY_CLOB/EMPTY_BLOB</strong></p>
<p>语法:EMPTY_CLOB()</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp; EMPTY_BLOB()</p>
<p>功能:获得一个空的LOB提示符(locator) .EMOTY_CLOB返回一个字符指示符,而EMPTY_BLOB返回一个二进制指示符, 用来对大数据类型字段进行初始化操作的函数.</p>
<p>使用位置:过程性语言和SQL语句.</p>
<p>&nbsp;</p>
<p>Select EMPTY_CLOB() from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>EXISTSNODE</strong></p>
<p>语法:EXISTSNODE(XMLType_instance,Xpatgh_string)</p>
<p>功能:9i新增，用于确认xml节点路径是否存在，返回0表示不存在，1表示存在。.</p>
<p>使用位置:过程性语言和SQL语句.</p>
<p>&nbsp;</p>
<p>Select EXISTSNODE(value(p),’/purchar/user’) from p;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>EXTRACT</strong></p>
<p>语法:EXTRACT (XMLType_instance,Xpatgh_string)</p>
<p>功能:9i新增，用于返回xml节点路径下的相应内容。.</p>
<p>使用位置:过程性语言和SQL语句.</p>
<p>&nbsp;</p>
<p>Select EXTRACT (value(p),’/purchar/user’) from p;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>EXTRACTVALUE</strong></p>
<p>语法:EXTRACTVALUE(XMLType_instance,Xpatgh_string)</p>
<p>功能:9i新增，用于返回xml节点路径下的值。.</p>
<p>使用位置:过程性语言和SQL语句.</p>
<p>&nbsp;</p>
<p>Select EXTRACTVALUE(value(p),’/purchar/user’) from p;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>GREATEST</strong></p>
<p>语法:GREATEST(expr1[,expr2]…)</p>
<p>功能:计算参数中最大的表达式.所有表达式的比较类型以expr1为准，比较字符的编码大小。</p>
<p>使用位置:过程性语言和SQL语句.</p>
<p>&nbsp;</p>
<p>SQL&gt; select greatest('AA','AB','AC') from dual;</p>
<p>&nbsp;</p>
<p>GR</p>
<p>AC</p>
<p>SQL&gt; select greatest('啊','安','天') from dual;</p>
<p>&nbsp;</p>
<p>GR</p>
<p>安</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>GREATEST_LB</strong></p>
<p>语法:GREATEST_LB(label1[,label2]…)</p>
<p>功能:返回标签(label)列表中最大的下界.每个标签必须拥有数据类型MLSLABEL、RAWMLSLABEL或者是一个表因字符串文字.函数只能用于truested oracle库.</p>
<p>使用位置:过程性语言和SQL语句.</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>LEAST</strong></p>
<p>语法:LEAST(expr1[,expr2]…)</p>
<p>功能:计算参数中最小的表达式.所有表达式的比较类型以expr1为准，比较字符的编码大小。</p>
<p>使用位置:过程性语言和SQL语句.</p>
<p>&nbsp;</p>
<p>SQL&gt; select least('啊','安','天') from dual;</p>
<p>&nbsp;</p>
<p>LE</p>
<p>啊</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>LEAST_UB</strong></p>
<p>语法:LEAST_UB(label1[,label2]…)</p>
<p>功能:与GREATEST_UB函数相似,本函数返回标签列表的最小上界.</p>
<p>使用位置:过程性语言和SQL语句.</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>NLS_CHARSET_DECL_LEN</strong></p>
<p>语法:NLS_CHARSET_DECL_LEN(byte_count,charset_id)</p>
<p>功能:该函数用于返回字节数在特定字符集中占有的字符个数。</p>
<p>&nbsp;</p>
<p>select NLS_CHARSET_DECL_LEN(200,nls_charset_id(‘zhs16gbkf1xed’)) from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>NLS_CHARSET_ID</strong></p>
<p>语法:NLS_CHARSET_ID(text)</p>
<p>功能:该函数用于返回字符集的ID号。</p>
<p>&nbsp;</p>
<p>select NLS_CHARSET_ID( ‘zhs16gbkf1xed’) from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>NLS_CHARSET_NAME</strong></p>
<p>语法:NLS_CHARSET_NAME(number)</p>
<p>功能:该函数用于返回字符集ID号所对应的字符集名。</p>
<p>&nbsp;</p>
<p>select NLS_CHARSET_NAME(852) from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>NULLIF</strong></p>
<p>语法:NULLIF (expr1, expr2) -&gt;相等返回NULL，不等返回expr1</p>
<p>功能：9i新增，用于比较表达式expr1和expr2，相等返回null，否则返回expr1.</p>
<p>Select nullif(expr1, expr2) from table_name;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>NVL</strong></p>
<p>语法:NVL (expr1, expr2)</p>
<p>功能:用于将NULL转变为实际值，如果expr1是NULL,那么返回expr2,否则返回expr1，expr1、expr2两者必须为同类型或expr2可以隐式转换为expr1，否则会报错。</p>
<p>&nbsp;</p>
<p>Select nvl(column_name,0) from tbale_name;</p>
<p>特别的date可以隐式转换为number，所以下面正确</p>
<p>SELECT NVL(to_date('2017-01-01','yyyy-mm-dd')-sysdate,SYSDATE)</p>
<p>&nbsp; FROM dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>NVL2</strong></p>
<p>语法:NVL2 (expr1, expr2, expr3)</p>
<p>功能:9i新增，expr1不为NULL，返回expr2；expr1为NULL，返回expr3。expr1可以是任意数据类型；expr2与expr3可以是除LONG外的任意数据类型，但需要类型一致或expr3可以隐式转换为expr2。</p>
<p>&nbsp;</p>
<p>特别的date可以隐式转换为number，所以下面正确</p>
<p>SELECT NVL2(to_date('01-jun-2016'),sysdate - to_date('01-jun-2016'),sysdate)</p>
<p>&nbsp; FROM dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>OVER</strong></p>
<p>语法：sun/count ( * )</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; over ( partition by XXX</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; order by XXX )</p>
<p>功能：此函数为分析函数，有别于本文介绍中的其他函数，更详细看本博客“分析函数”专题</p>
<p>使用位置：过程性语言和SQL语句</p>
<p>&nbsp;</p>
<p>sum(sal) over (partition by deptno order by ename)</p>
<p>&nbsp;</p>
<p>COUNT( * )</p>
<p>OVER (</p>
<p>PARTITION BY class_id</p>
<p>ORDER BY ROWNUM</p>
<p>ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)</p>
<p>COUNT( * )</p>
<p>OVER (PARTITION BY e.phone</p>
<p>ORDER BY pp.sort, qs.user_id DESC, ROWNUM</p>
<p>ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>PATH</strong></p>
<p>语法:PATH(correction_integer)</p>
<p>功能:9i新增，用于返回特定XML资源所对应的相对路径。</p>
<p>&nbsp;</p>
<p>Select path(1),depth(2) from table_name;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>SYS_CONNECT_BY_PATH</strong></p>
<p>语法:SYS_CONNECT_BY_PATH(column,char)</p>
<p>功能:9i新增（只适用于层次查询），用于返回从根到节点的列值路径。</p>
<p>&nbsp;</p>
<p>Select lpad(‘ ‘,2*level-1)||sys_connect_by_path(ename,’/’) from table_name start with ename=’scott’ connect by prior empno=mgr;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>SYS_CONTEXT</strong></p>
<p>语法：sys_coniext(‘context’,’attribute’)</p>
<p>功能：该函数用于返回应用上下文的特定属性值，获得系统信息，其中context为上下文名，而attribute为应用上下文名，此函数可以得到oracle主机及客户端的信息。</p>
<p>&nbsp;</p>
<p>SELECT&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'TERMINAL') 客户端名称,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'LANGUAGE') 客户端语言,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'SESSIONID') sessionid,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'INSTANCE') instance,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'ENTRYID') entryid,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'ISDBA') isdba,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'NLS_TERRITORY') 地区,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'NLS_CURRENCY') 货币,</p>
<p>&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SYS_CONTEXT ('USERENV', 'NLS_CALENDAR') nls_calendar,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'NLS_DATE_FORMAT') 时间格式,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'NLS_DATE_LANGUAGE') 时间语言,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'NLS_SORT') nls_sort,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'CURRENT_USER') current_user,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'CURRENT_USERID') current_userid,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'SESSION_USER') session_user,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'SESSION_USERID') session_userid,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'PROXY_USER') proxy_user,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'PROXY_USERID') proxy_userid,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'DB_DOMAIN') db_domain,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'DB_NAME') 数据库名称,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'HOST') 客户端完成名称,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'OS_USER') 客户端用户,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'EXTERNAL_NAME') external_name,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'IP_ADDRESS') 客户端IP地址,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'NETWORK_PROTOCOL') 网络协议,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'BG_JOB_ID') bg_job_id,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'FG_JOB_ID') fg_job_id,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'AUTHENTICATION_TYPE') authentication_type,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SYS_CONTEXT ('USERENV', 'AUTHENTICATION_DATA') authentication_data</p>
<p>&nbsp; FROM&nbsp;&nbsp; DUAL</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>SYS_DBURIGEN</strong></p>
<p>语法:SYS_DBURIGEN(column)</p>
<p>功能:9i新增，根据列或属性生产类型为DBUriType的URL。</p>
<p>&nbsp;</p>
<p>Select SYS_DBURIGEN(ename) from emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>SYS_GUID</strong></p>
<p>语法:SYS_GUID()</p>
<p>功能:该函数用于生产类型为RAW的16字节的唯一标识符，每次调用该函数都会发生不同的RAW数据。</p>
<p>&nbsp;</p>
<p>Select SYS_GUID() from emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>SYS_TYPEID</strong></p>
<p>语法:SYS_TYPEID(object_type_value)</p>
<p>功能:该函数用于返回唯一的类型ID值。</p>
<p>&nbsp;</p>
<p>Select name, SYS_TYPEID(value(p)) from emp p;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>SYS_XMLAGG</strong></p>
<p>语法:SYS_XMLAGG(expr[,fmt])</p>
<p>功能:9i新增，用户汇总所有XML文档，并生成一个XML文档。</p>
<p>&nbsp;</p>
<p>Select SYS_XMLAGG(sys_xmlgen(ename)) from emp p;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>SYS_XMLGEN</strong></p>
<p>语法:SYS_XMLGEN(expr[,fmt])</p>
<p>功能:9i新增，根据数据库表的行和列生成一个XMLType实例。</p>
<p>&nbsp;</p>
<p>Select sys_xmlgen(ename) from emp p;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>UID</strong></p>
<p>语法:UID</p>
<p>功能:获得当前数据库用的惟一标识,标识是一个整数.</p>
<p>使用位置:过程性语言和SQL语句.</p>
<p>&nbsp;</p>
<p>SQL&gt; show user</p>
<p>USER 为"GAO"</p>
<p>SQL&gt; select username,user_id from dba_users where user_id=uid;</p>
<p>&nbsp;</p>
<p>USERNAME&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; USER_ID</p>
<p>GAO&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 25</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>UPDATEXML</strong></p>
<p>语法:UPDATEXML(XMLType_instance,Xpath_string,value_expr)</p>
<p>功能:9i新增，用于更新特定XMLType实例相对应节点路径的内容。</p>
<p>&nbsp;</p>
<p>Update xmltable p set p=updatexml(value(p),’/pruch/user/text()’,’scott’)</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>USER</strong></p>
<p>语法:USER</p>
<p>功能:取得当前oracle用户的名字,返回的结果是一个VARCHAR2型字符串.</p>
<p>使用位置:过程性语言和SQL语句.</p>
<p>SQL&gt; select user from&nbsp; dual;</p>
<p>&nbsp;</p>
<p>USER</p>
<p>GAO</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>USERENV</strong></p>
<p>语法:USERENV(option)</p>
<p>功能:根据参数option,取得一个有关当前会话信息的VARCHAR2数值.</p>
<p>使用位置:过程性语言和SQL语句.</p>
<p>返回当前用户环境的信息,opt可以是:</p>
<p>ENTRYID,SESSIONID,TERMINAL,ISDBA,LABLE,LANGUAGE,CLIENT_INFO,LANG,VSIZE</p>
<p>OPTION='ISDBA'若当前是DBA角色,则为TRUE,否则FALSE.</p>
<p>OPTION='LANGUAGE'返回数据库的字符集.</p>
<p>OPTION='SESSIONID'为当前会话标识符.</p>
<p>OPTION='ENTRYID'返回可审计的会话标识符.</p>
<p>OPTION='LANG'返回会话语言名称的ISO简记.</p>
<p>OPTION='INSTANCE'返回当前的实例.</p>
<p>OPTION='terminal'返回当前计算机名</p>
<p>ISDBA&nbsp; 查看当前用户是否是DBA如果是则返回true</p>
<p>SQL&gt; select userenv('isdba') from dual;</p>
<p>USEREN</p>
<p>FALSE</p>
<p>&nbsp;</p>
<p>SESSION返回会话标志</p>
<p>SQL&gt; select userenv('sessionid') from dual;</p>
<p>USERENV('SESSIONID')</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 152</p>
<p>&nbsp;</p>
<p>ENTRYID返回会话人口标志</p>
<p>SQL&gt; select userenv('entryid') from dual;</p>
<p>USERENV('ENTRYID')</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</p>
<p>INSTANCE返回当前INSTANCE的标志</p>
<p>SQL&gt; select userenv('instance') from dual;</p>
<p>USERENV('INSTANCE')</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1</p>
<p>&nbsp;</p>
<p>LANGUAGE返回当前环境变量，包括语言、地区、字符集</p>
<p>SQL&gt; select userenv('language') from dual;</p>
<p>USERENV('LANGUAGE')</p>
<p>SIMPLIFIED CHINESE_CHINA.ZHS16GBK</p>
<p>&nbsp;</p>
<p>LANG返回当前环境的语言的缩写</p>
<p>SQL&gt; select userenv('lang') from dual;</p>
<p>USERENV('LANG')</p>
<p>ZHS</p>
<p>&nbsp;</p>
<p>TERMINAL返回用户的终端或机器的OS标示符</p>
<p>SQL&gt; select userenv('terminal') from dual;</p>
<p>USERENV('TERMINA</p>
<p>GAO</p>
<p>&nbsp;</p>
<p>CLIENT_INFO 返回由包DBMS_APPLICATION_INFO所存储的用户会话信息（64字节）</p>
<p>Select userenv(‘CLIENT_INFO’) from dual;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>VSIZE</strong></p>
<p>语法:VSIZE(value)</p>
<p>功能:获得value的内部表示的字节数.如果value是NULL,结果是NULL.</p>
<p>使用位置: SQL语句.</p>
<p>&nbsp;</p>
<p>SQL&gt; select vsize(user),user from dual;</p>
<p>VSIZE(USER) USER</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 6 SYSTEM</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>XMLAGG</strong></p>
<p>语法:XMLAGG(XMLType_instance [order by sort_list])</p>
<p>功能:9i新增，用于汇总多个XML块，并生成XML文档。</p>
<p>&nbsp;</p>
<p>Select xmlagg(xmlelement(“employee”,ename||’ ’||sal)) from emp where deptno=10;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>XMLCOLATTVAL</strong></p>
<p>语法:XMLCOLATTVAL(value_expr1[,value_expr2]…)</p>
<p>功能:9i新增，用于生成XML块，并增加”column”作为属性名。</p>
<p>&nbsp;</p>
<p>Select xmlelement(“emp”, XMLCOLATTVAL(ename,sall)) from emp where deptno=10;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>XMLCONCAT</strong></p>
<p>语法:XMLCONCAT(XMLType_instance1[,XMLType_instance2]…)</p>
<p>功能:9i新增，用于连接多个XMLType实例，并生成一个新的XMLType实例。</p>
<p>&nbsp;</p>
<p>Select XMLCONCAT(xmlelement(‘ename’,ename), xmlelement(‘sal’,sal)) from emp where deptno=10;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>XMLELEMENT</strong></p>
<p>语法:XMLELEMENT(identifier[,xml_attribute_clause][,value_expr])</p>
<p>功能:9i新增，用于返回XMLType实例，其中参数identifier指定元素名，参数xml_attribute_clause指定元素属性子句，参数value_expr指定元素值。</p>
<p>&nbsp;</p>
<p>Select XMLELEMENT(‘date’,sysdate) from dual;</p>
<p>&nbsp;</p>
<p>Select XMLELEMENT(“emp”,xmlattributes(empno as “id”,ename)) from emp;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>XMLFOREST</strong></p>
<p>语法:XMLPOREST(value_expr1[,value_expr2]…)</p>
<p>功能:9i新增，用于返回XML块。</p>
<p>&nbsp;</p>
<p>Select xmlelement(‘ename’, XMLPOREST[ename,sal]) from emp where deptno=10;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>XMLSEQUENCE</strong></p>
<p>语法:XMLSEQUENCE(xmltype_instance)</p>
<p>功能:9i新增，用于返回xmltype实例中顶级节点一下的varray元素。</p>
<p>&nbsp;</p>
<p>Select XMLSEQUENCE(extract(value(x),’/purorder/line/*’)) from emp p where deptno=10;</p>
<p>--------------------------------------------------</p>
<p>&nbsp;</p>
<p><strong>XMLTRANSFORM</strong></p>
<p>语法:XMLTRANSFORM(xmltype_instance,xsl_ss)</p>
<p>功能:9i新增，用于将xmltype实例按照XSL样式进行转换，并生成新的xmltype实例。</p>
<p>&nbsp;</p>
<p>Select XMLTRANSFORM(w.warehouse_spec,x.coll).getclobval from warehouse w,xsl_tab x where w.name=x.name;</p>
<p>--------------------------------------------------</p>
<
