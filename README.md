## Introduction
REST API Common Framework base on JAX-RS.  

Provide the following functions:  

* Exception Mapping (錯誤處理機制，包括 HTTP Status 400、500 之錯誤)
* XSS Filter, Utils, JsonDeserialize
* CORS Filter
* Success Filter
* Paging
	* CursorPagingModel 游標型分頁，搭配 CursorUtils 對游標加解密編碼
	* OffsetPagingModel 位移型分頁

## Framework

* [JAX-RS](https://zh.wikipedia.org/wiki/JAX-RS): Java API for RESTful Web Services
* [ESAPI](https://www.owasp.org/index.php/Category:OWASP_Enterprise_Security_API): [OWASP](https://www.owasp.org/index.php/Main_Page) Enterprise Security API
* [Swagger-Annotations](https://github.com/swagger-api/swagger-core/wiki/Annotations)

## Usage

1. dependencies

	```
	dependencies {
		compile group: 'idv.villebez.api', name: 'rest-api-base', version: '0.3.0'
	}
	```
	
2. jersey example

	```
	<servlet>
		<servlet-name>Jersey</servlet-name>
		<servlet-class>org.glassfish.jersey.servlet.ServletContainer</servlet-class>
		<init-param>
			<param-name>jersey.config.server.provider.packages</param-name>
			<param-value>
				idv.villebez.exception.mapper,
				idv.villebez.filter
        		</param-value>
		</init-param>
		<load-on-startup>1</load-on-startup>
	</servlet>
	```
	
## XSS

### Jackson JsonDeserialize Annotation
```
@JsonDeserialize(using = XSSDeserializer.class)
```

### Utils
```
value = XSSUtils.stripSpecificXSS(value);
value = XSSUtils.stripXSS(value);
```

	
## Example Project

* [JAX-RS](example/JAX-RS/)
* [Jersey](example/jersey2/)
* [Jersey + Spring + Swagger](example/jersey_spring_swagger/)
