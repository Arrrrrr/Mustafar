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

## XSL (death-star.xsl)

A file that converts XML into another file format, such as HTML or PDF. Information architects develop XSL files, and then run XML and XSL files together in an XSL processor (such as Saxon or Xalan) to produce output. 

## ANT (ant-death-star.xml)

An ant script is a tool information architects use to run XML and XSL files together in an XSL processor (other tools include the Command Line Interface or oXygen XML Editor). This Ant script was created to be run in Eclipse, and to run the files death-star.xml and death-star.xsl though the Saxon XSL processor to output death-star.html.

## HTML (death-star.html)

Output result of the publishing process.

## CSS (death-star.css)

Information architects develop CSS to style HTML files.
