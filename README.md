# Publishing = FUN

How much fun? Just keep scrolling to find out.

## DTD

A DTD structures your XML. A DTD tells your XML file which element tags it is allowed to use. Information architects develop DTDs to control the structure of content.

```markdown
example - death-star.dtd

<?xml version="1.0" encoding="UTF-8"?>

<!ELEMENT deathstar (name,summary,assets+)>
    <!ELEMENT name (#PCDATA)>
    <!ELEMENT summary (#PCDATA)>
    <!ELEMENT assets (weapons+,sithlords+,admirals+)>
       <!ELEMENT weapons (weapon+)>
            <!ELEMENT weapon (#PCDATA)>
       <!ELEMENT sithlords (master,apprentice)>
            <!ELEMENT master (#PCDATA)>
            <!ELEMENT apprentice (#PCDATA)>
        <!ELEMENT admirals (admiral+)>
            <!ELEMENT admiral (#PCDATA)>
```

## XML

A file written in element tags. Its structure is controlled by the DTD. Authors write content in XML files.


```markdown
example - death-star.xml

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE deathstar SYSTEM "death-star.dtd">
<deathstar>
    <name>The Death Star</name>
    <summary>A powerful weapon that can destroy entire planets</summary>
    <assets>
        <weapons>
            <weapon>Super laser</weapon>
            <weapon>TIE fighters</weapon>
            <weapon>Light sabers</weapon>
            <weapon>Turbo lasers</weapon>
        </weapons>
        <sithlords>
            <master>Darth Sidious</master>
            <apprentice>Darth Vader</apprentice>
        </sithlords>
        <admirals>
            <admiral>Tarkin</admiral>
            <admiral>Motti</admiral>
            <admiral>Tagge</admiral>
        </admirals>
    </assets>
</deathstar>
```

## XSL

A file that converts XML into another file format, such as HTML or PDF. Information architects develop XSL files, and then run XML and XSL files together in an XSL processor (such as Saxon or Xalan) to produce output. 

```markdown
example - death-star.xsl

<?xml version="1.0" encoding="UTF-8"?>
<!-- number-lotr-01.xsl -->
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
    xmlns:xs="http://www.w3.org/2001/XMLSchema"
    exclude-result-prefixes="xs"
    version="2.0">
    
    <xsl:output method="html"/>
    
    <xsl:template match="deathstar">
        <html>
            <head>
                <title>Death star information</title>
                <link rel="stylesheet" href="death-star.css"/>
            </head>
            <body>
                    <h1>
                        <xsl:value-of select="name"/>
                    </h1>
                    <p>
                        <xsl:value-of select="summary"/>
                    </p>
                    <h2>Weapons</h2>
                    <ul>
                        <xsl:for-each select="assets/weapons/weapon">
                            <li>
                                <xsl:value-of select="."/>
                            </li>
                        </xsl:for-each>
                    </ul>
                    <h2>Sith Lords</h2>
                    <ul>
                        <xsl:for-each select="assets/sithlords/master">
                            <li>The Master: <xsl:value-of select="."/></li>
                        </xsl:for-each>
                        <xsl:for-each select="assets/sithlords/apprentice">
                            <li>The Apprentice: <xsl:value-of select="."/></li>
                        </xsl:for-each>
                    </ul>
                    <h2>Admirals</h2>
                    <ul>
                        <xsl:for-each select="assets/admirals/admiral">
                            <li>
                                <xsl:value-of select="."/>
                            </li>
                        </xsl:for-each>
                    </ul>
              </body>
        </html>
    </xsl:template>
    
</xsl:stylesheet>
```

## ANT

An ant script is a tool information architects use to run XML and XSL files together in an XSL processor (other tools include the Command Line Interface or oXygen XML Editor). This Ant script was created to be run in Eclipse, and to run the files death-star.xml and death-star.xsl though the Saxon XSL processor to output death-star.html.

```markdown
example - ant-death-star.xml

<?xml version="1.0" encoding="UTF-8" ?>
<project name="sample_xhtml" default="test-saxon">
	
	<target name="test-saxon">
		<xslt classpath="lib\saxon8.jar"
			in="death-star.xml" 
			out="death-star.html" 
			style="death-star.xsl">
			<factory name="net.sf.saxon.TransformerFactoryImpl"/>
		</xslt>
	</target>

</project>
```

## HTML

Output result of the publishing process.

```markdown
example - death-star.html

<html>
   <head>
      <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
      <title>Death star information</title>
      <link rel="stylesheet" href="death-star.css">
   </head>
   <body>
      <h1>The Death Star</h1>
      <p>A powerful weapon that can destroy entire planets</p>
      <h2>Weapons</h2>
      <ul>
         <li>Super laser</li>
         <li>TIE fighters</li>
         <li>Light sabers</li>
         <li>Turbo lasers</li>
      </ul>
      <h2>Sith Lords</h2>
      <ul>
         <li>The Master: Darth Sidious</li>
         <li>The Apprentice: Darth Vader</li>
      </ul>
      <h2>Admirals</h2>
      <ul>
         <li>Tarkin</li>
         <li>Motti</li>
         <li>Tagge</li>
      </ul>
   </body>
</html>
```

## CSS

Information architects develop CSS to style HTML files.

```markdown
example - death-star.css

body {
    background-color: black;
    font-family: consolas, "Lucida Console", Monaco, monospace;
    color: red;
    text-shadow: 0px 0px 5px white;
}
```
