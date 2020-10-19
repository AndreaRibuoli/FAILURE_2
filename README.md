# FAILURE_2
Missing BUILD CL source 

When installed with PASERIE/INSTALL will fail because of missing BUILD CL source file.
The installer will test compilation for an ILE CL and, should it fail, for an OPM CL.

Being declared in **GUIDANCE.TXT** the installer will request the transfering of **QCLSRC/BUILD** source. 

Using `VERBOSE('Y')` option will help identifying the issue:

```
> GET /repos/AndreaRibuoli/FAILURE_2/contents/QCLSRC/BUILD.CLLE HTTP/1.1     
Host: api.github.com                                                         
User-Agent: curl/0007.0073.0000                                              
Accept: application/vnd.github.v3.raw                                        
Authorization: token xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx                
* old SSL session ID is stale, removing                                      
* Mark bundle as not supporting multiuse                                     
< HTTP/1.1 404 Not Found                                                     
```

Alternatively you can use the `DEVOPT('Y')` option.

```
PASERIE/INSTALL GIT_USER(AndreaRibuoli) PACKAGEN(FAILURE_2) DEVOPT('Y')
```

Two spools will be generated (ILE CL, OPM CL) complaining with invalid CL source:

```
      1- {                                                                 
* CPD0018 30  String '{         ' contains a character that is not valid.  
      2-   "message": "Not Found",                                         
* CPD0020 30  Character ':' not valid following string '"message" '.       
* CPD0020 30  Character ' ' not valid following string '"Not      '.       
* CPD0018 30  String 'FOUND",   ' contains a character that is not valid.  
```

The content is actually returned as text that gets saved as CL source failing during compilation... (`{ "message": "Not Found", ...`).


