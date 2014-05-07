## Context.PROVIDER_URL的写法 ##
### WebSphere           
	Context.INITIAL_CONTEXT_FACTORY             
	  "com.ibm.websphere.naming.WsnInitialContextFactory"             
	Context.PROVIDER_URL             
	  "iiop://localhost:900"             
  
### Weblogic        
	Context.INITIAL_CONTEXT_FACTORY             
	          "weblogic.jndi.WLInitialContextFactory"             
	Context.PROVIDER_URL             
	          "t3://127.0.0.1:7001"
                 
### J2EE SDK(J2EE RI)
            
	Context.INITIAL_CONTEXT_FACTORY             
	          "com.sun.jndi.cosnaming.CNCtxFactory"             
	Context.PROVIDER_URL             
	          "iiop://127.0.0.1:1050"             
      
### SilverStream
         
	Context.INITIAL_CONTEXT_FACTORY             
	  "com.sssw.rt.jndi.AgInitCtxFactory"             
	Context.PROVIDER_URL             
	  "sssw://localhost:80"             
    
### OC4J     
	Context.INITIAL_CONTEXT_FACTORY     
	"com.evermind.server.rmi.RMIInitialContextFactory"     
	Context.PROVIDER_URL     
	"ormi://127.0.0.1/" 
  
### JBOSS     
	java.naming.factory.initial     
	"org.jnp.interfaces.NamingContextFactory"     
	java.naming.provider.url     
	"localhost:1099" 
        
### WAS5     
	Context.INITIAL_CONTEXT_FACTORY             
	  "com.ibm.websphere.naming.WsnInitialContextFactory"             
	Context.PROVIDER_URL             
	  "iiop://localhost:2809"  