# some notes re the DBNL TEI XML

## example 1: _gid001186201_01.xml

- this is from _de Gids_, a literary journal
- each article sits in a `<div type="chapter">` 
- but the only numbered elements are <pb n="1"/>
- I don't understand the meaning of `<interpGrp>` (but I hope it somehow leads us to article level metadata)
- **To only thing we can refer to is the page. This requires knowledge of the issue, which will need to come from the metadata in the teiHeader**
- there is this in the CSV, but it's on title level, not on article level: `_gid001186201|"De Gids. Jaargang 26"||"1862"|"1ste druk"||"leide001dbnl01"|"1"|"1862"|"_gid001"|||"[tijdschrift] Gids`
- a CTS URN of the _article_ would look like ????
- a CTS URN of the _page_ would look like ???? `urn:cts:dutchLit:gid001186201.gid001gids01:1` which _I think_ only identifies volume and page
- cf. the DBNL URL `https://dbnl.org/tekst/_gid001186201_01/_gid001186201_01_0001.php` which seems to also identify the article ("entry")

J. Margadant, "Een Teeken des tijds", _De Gids_ 26.1 (1862), pp. 1-26

```xml
<text>
    <interpGrp>
        <interp type="primair" value="_gid001186201"/> 
        <interp type="primair" value="_gid001gids01"/> 
    </interpGrp>   
 <body>
     <div type="chapter">
         <interpGrp>
             <interp type="primair" value="marg004"/>
             <interp type="secundair" value="frank01"/>
         </interpGrp>
     <pb n="1"/>
     <head rend="h3">Een teeken des tijds.</head>
     <p>Reeds zijn er tien jaren verloopen
```

## example 2: razo001laat01_01.xml

- structure seems similar to the example above: only the pages (or rather, page beginnings) are numbered. All other information is in the metada, but some of it is machine-readable, as in `<interp>`
- for `<interp>` see https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-interp.html. 
- razo001laat01 reveals this in the CSV: `razo001laat01|"Het laatste aardige prentenboek"||"1863"|"1ste druk"|"393214540"|"denha004koni01"|"1"|"1863"|"razo001"|"W.P."||"Razoux"|"1818"|"1871"|"6 augustus"|"4 december"|"Zwolle"|"Boston`

```xml
 <text>
    <interpGrp>
        <interp type="primair" value="razo001laat01"/>
    </interpGrp>   
    <body>
        <div type="chapter">
            <pb n="3"/>
            <head rend="h3">Hannes Haas.</head>
            <p><figure><p><xptr to="razo001laat01ill01.gif"/></p></figure></p>
            <lg type="poem">
                <l>Hannes, met zijn tasch belaân,</l>
```