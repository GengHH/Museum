#这里是对js的常见正则表达式的一个集合

##纯数字相关

  - 正整数
  
      + 包括0的纯正整数
      
       *  var reg = /^[0-9]*[1-9][0-9]*$/　　//正整数 
       *  var reg = /^[1-9]\d*|0$/        //非负整数（正整数 + 0） 
      + 不包括0的正整数
      
      + 小于某一特定值的包含0的正整数
      
      + 小于等于某一特定值的包含0的正整数
      
  - 正浮点型
  
      + 保留特定小数位的浮点数（必须有这么多位的小数）
       
        *  var reg = /^\+?(\d*\.\d{X})$/;
        *  var str = ".12";
        *  reg.test(str)
        
        **x就是需要保留的小数点偶的位数的个数，匹配成功返回true，失败返回false**
        
      + 小于等于特定位数的浮点数（包含0和整数）
  
  - 负整数

      + 包括0的负整数
         *  "^-[0-9]*[1-9][0-9]*$"　　//负整数 
      + 不包括0的负整数

      + 小于某一特定值的包含0的负整数

      + 小于等于某一特定值的包含0的负整数

  - 负浮点型
  
       + 负浮点数
       
       　 *  var reg = /^-([1-9]\d*\.\d*|0\.\d*[1-9]\d*)$/
       + 保留特定小数位的负浮点数（必须有这么多位的小数）
      
       + 小于等于特定位数的负浮点数（包含0和负整数）
    - 浮点数    
         *  var reg = /^(-?\d+)(\.\d+)?$/
  - 大陆内地手机号

      + 包含所有的开头
          
         * reg = /^1[3458][0-9]\d{8}$/;
         
      + 校验普通电话、传真号码：可以“+”开头，除数字外，可含有“-” 
      
          function isTel(s) 
          { 
          //var patrn=/^[+]{0,1}(\d){1,3}[ ]?([-]?(\d){1,12})+$/; 
          var patrn=/^[+]{0,1}(\d){1,3}[ ]?([-]?((\d)|[ ]){1,12})+$/; 
          if (!patrn.exec(s)) return false 
          return true 
          }
       + 校验手机号码：必须以数字开头，除数字外，可含有“-” 
          function isMobil(s) 
          { 
          var patrn=/^[+]{0,1}(\d){1,3}[ ]?([-]?((\d)|[ ]){1,12})+$/; 
          if (!patrn.exec(s)) return false 
          return true 
          }
       
   - 邮箱
     
       + 所有邮箱
       
           * reg = /^(\w-*\.*)+@(\w-?)+(\.\w{2,})+$/;
          
        
       + qq邮箱
     
   - 常见类型密码
      
     + 校验是否全由数字组成 
        function isDigit(s) 
        { 
          var patrn=/^[0-9]{1,20}$/; 
          if (!patrn.exec(s)) 
            return false 
          return true 
        }
     + 校验登录名：只能输入5-20(或者n-m)个以字母开头、可带数字、“_”、“.”的字串 
      function isRegisterUserName(s) 
      { 
        var patrn=/^[a-zA-Z]{1}([a-zA-Z0-9]|[._]){4,19}$/; 
        if (!patrn.exec(s)) 
          return false 
        return true 
      }
     + 校验用户姓名：只能输入1-30(或者n-m)个以字母开头的字串 
      function isTrueName(s) 
      { 
        var patrn=/^[a-zA-Z]{1,30}$/; 
        if (!patrn.exec(s)) 
          return false 
        return true 
      }
     + 校验密码：只能输入6-20 (或者n-m)个字母、数字、下划线 
      function isPasswd(s) 
      { 
        var patrn=/^(\w){6,20}$/; 
        if (!patrn.exec(s)) 
          return false 
        return true 
      }

   - 校验邮政编码 (有待验证)
   
       function isPostalCode(s) 
        { 
          //var patrn=/^[a-zA-Z0-9]{3,12}$/; 
          var patrn=/^[a-zA-Z0-9 ]{3,12}$/; 
          if (!patrn.exec(s)) 
            return false 
          return true 
        }
    - 校验搜索关键字 
    
        function isSearch(s) 
        { 
          var patrn=/^[^`~!@#$%^&*()+=|\\\][\]\{\}:;'\,.<>/?]{1}[^`~!@$%^&()+=|\\\][\]\{\}:;'\,.<>?]{0,19}$/;
          if (!patrn.exec(s)) 
            return false 
          return true 
        }

    - 校验IP地址
    
        function isIP(s) 
        { 
          var patrn= 
          if (!patrn.exec(s)) 
            return false 
          return true 
        } 
    - 常用字符串
    
        + 由26个英文字母组成的字符串 (包括大小写)
          *  var reg = /^[A-Za-z]+$/　　
        + 由26个英文字母的大写组成的字符串 
          *  var reg=/^[A-Z]+$/　　
        + 由26个英文字母的小写组成的字符串
          *  var reg=/^[a-z]+$/　　 
        + 由数字和26个英文字母组成的字符串
          *  var reg=/^[A-Za-z0-9]+$/
        + 汉字
          *  var reg=/^[\u4e00-\u9fa5]{0,}$/   
        + 禁止输入含有~的字符：
          *  var reg=/[^~\x22]+/ 

          (是字符不是包含~的字符串)

   - 匹配国内电话号码:
    评注：匹配形式如 0511-4405222 或 021-87888822

    - 匹配腾讯QQ号：
    评注：腾讯QQ号从10000开始

    - 匹配中国邮政编码：
    评注：中国邮政编码为6位数字

    - 匹配身份证：
    15或18位身份证：
    15位身份证：^[1-9]\d{7}((0\d)|(1[0-2]))(([0|1|2]\d)|3[0-1])\d{3}$
    18位身份证：
          var pat = /^\d{17}[\dxX]$/;
        var pat1 = /^\d{17}[0-9xX]$/;
        var pat2 = /^\d{17}[0-9x]$/i; //i忽略大小写
    - email地址 
    - url 
    
###正则中常用到的方法 
**compile方法**
编译一个正则表达式对象
**exec方法**
运行正则表达式匹配
**test方法**
测试正则达式匹配
**toSource方法** 
返回一个对象的文字描述指定的对象；你可以使用这个值来建立一个新的对象。不考虑Object.toS 
**ource方法**
**toString方法** 
返回一个字符串描述指定的对象，不考虑Object.toString对象。
**valueOf方法**
返回指定对角的原始值。不考虑Object.valueOf方法。
另外，这个对象继承了对象的watch和unwatch方法
      
      
###例子： 
例１、下述示例脚本使用replace方法来转换串中的单词。在替换的文本中，脚本使用全局 RegExp对象的$1和$2属性的值。
注意，在作为第二个参数传递给replace方法的时候，RegExp对象的$属性的名称。 
<SCRIPT LANGUAGE="JavaScript1.2"> 
re = /(\w+)\s(\w+)/; 
str = "John Smith"; 
newstr=str.replace(re,"$2, $1"); 
document.write(newstr) 
</SCRIPT>
显示结果："Smith, John".
例２、下述示例脚本中，RegExp.input由Change事件处理句柄设置。在getInfo函数中，exec 方法 
使用RegExp.input的值作为它的参数，注意RegExp预置了$属性。

<SCRIPT LANGUAGE="JavaScript1.2"> 
function getInfo(abc) 
{ 
re = /(\w+)\s(\d+)/; 
re.exec(abc.value); 
window.alert(RegExp.$1 + ", your age is " + RegExp.$2); 
} 
</SCRIPT>
　　请输入你的姓和年龄，输入完后按回车键。 
　　 <FORM><INPUT TYPE="TEXT" NAME="NameAge" onChange="getInfo(this);"></FORM> 
　　 </HTML>
$1, ..., $9属性 
用圆括号括着的匹配子串，如果有的话。 
是RegExp的属性 
静态，只读
在JavaScript 1.2, NES 3.0以上版本提供 
描述：因为input是静态属性，不是个别正则表达式对象的属性。你可以使用RegExp.input 访问该属性。
能加上圆括号的子串的数量不受限制，但正则表达式对象只能保留最后9 条。如果你要访问所有的圆括号内的匹配字串，你可以使用返回的数组。
这些属性能用在RegExp.replace方法替换后的字符串(输出结果)。当使用这种方式的时候，不用预 先考虑RegExp对象。
下面给出例子。当正则表达式中没有包含圆括号的时候，该脚本解释成$n的字面意义。(这里的n是一个正整数)。
例如： 
下例脚本使用replace 方法来交换串中单词的位置。在替换后的文本字串中，脚本使用正则表达式 
RegExp对象的$1和$2属性的值。注意：当它们向replace方法传递参数的时候，这里没有考虑 $ 属性的 
RegExp对象的名称。 
<SCRIPT LANGUAGE="JavaScript1.2"> 
re = /(\w+)\s(\w+)/; 
str = "John Smith"; 
newstr=str.replace(re,"$2, $1"); 
document.write(newstr) 
</SCRIPT> 
显示的输出结果为：Smith, John。
            
###自定义正则表达式构造器的建立方法： 
文字格式或RegExp构造器函数。 
文字建立格式使用以下格式： 
/pattern/flags即/模式/标记
构造器函数方法使用方法如下： 

new RegExp("pattern"[, "flags"])即new RegExp("模式"[,"标记"])

参数： 
pattern(模式) 
表示正则表达式的文本
flags(标记) 
如果指定此项，flags可以是下面值之一： 
g: global match(全定匹配) 
i: ignore case(忽略大小写) 
gi: both global match and ignore case(匹配所有可能的值，也忽略大小写)
注意：文本格式中的参数不要使用引号标记，而构造器函数的参数则要使用引号标记。所以下面的表达式建立同样的正则表达式： 
/ab+c/i 
　　 new RegExp("ab+c", "i")
描述： 
当使用构造函数的时候，必须使用正常的字符串避开规则(在字符串中加入前导字符\ )是必须的。 
例如，下面的两条语句是等价的： 
re = new RegExp("\\w+") 
re = /\w+/
