#### 1. Add the attached jar files for LUCENE-5205 and SOLR-5410 in the following location on all Solr server nodes to guarantee it's in the classpath:
`/opt/cloudera/parcels/CDH-6.3.1-1.cdh6.3.1.p0.1470567/lib/solr/server/solr-webapp/webapp/WEB-INF/lib`

#### 2. Restart Solr service

#### 3. Edit your solrconfig.xml:

FIND:
```xml
<!-- Query Parsers

       https://lucene.apache.org/solr/guide/query-syntax-and-parsing.html

       Multiple QParserPlugins can be registered by name, and then
       used in either the "defType" param for the QueryComponent (used
       by SearchHandler) or in LocalParams
    -->
  <!-- example of registering a query parser -->
  <!--
     <queryParser name="myparser" class="com.mycompany.MyQParserPlugin"/>
    -->
```

ADD AFTER:
```xml
<queryParser name="span" class="org.tallison.solr.search.SpanQParserPlugin" />
```
