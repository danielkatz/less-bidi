LESS-bidi - Direction agnostic stylesheets
=========

LESS-bidi is a set of LESS mixins that allows creating bi-directional styling without significant code duplication. <br/>
By using LESS-bidi mixins, it’s possible to create direction agnostic CSS stylesheets, which are faster to write and much easier to maintain.
Moreover, the naming convention used throughout the mixins makes it easier to comprehend by keeping the naming of properties as close as possible to the original CSS property names. <br/>


Paradigm shift
--------------
Direction agnostic styling is made possible by using a new approach of referring to both sides of a document as the “start” and “end” of the text as opposed to “left” or “right” of the document. This approach is similar to what is done in flex-box specification (although LESS-bidi does not use or depend on flex-box). 
The interpretation of the terms *start* and *end* depends on the value of the variable @bidi; when the value is **ltr** than *start* is **left** and *end* is **right**, and when the value is **rtl** it will be exactly the opposite.


For example:
<table>
<tr>
<th>
LESS-bidi
</th>
<th>
CSS
</th>
</tr>
<tr>
<td>
<pre>
@import "bidi/bidi";

.ltr {
    .style(ltr);
}
.rtl {
    .style(rtl);
}
.style(@bidi) {
    body{
		.bidi-direction();
	}

    h1 {
        .bidi-margin-start(20px);
		margin-bottom: 10px;
    }
    .two-col article {
        .bidi-float(start);
    }
    .two-col nav {
        .bidi-float(end);
    }
}
</pre>
</td>
<td>
<pre>
.ltr body {
  direction: ltr;
}
.ltr h1 {
  margin-left: 20px;
  margin-bottom: 10px;
}
.ltr .two-col article {
  float: left;
}
.ltr .two-col nav {
  float: right;
}

.rtl body {
  direction: rtl;
}
.rtl h1 {
  margin-right: 20px;
  margin-bottom: 10px;
}
.rtl .two-col article {
  float: right;
}
.rtl .two-col nav {
  float: left;
}
</pre>
</td>
</tr>
</table>
