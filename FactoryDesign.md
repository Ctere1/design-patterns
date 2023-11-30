## Factory Design Pattern
- The factory design pattern is used when we have a superclass with multiple sub-classes and based on input, we need to return one of the sub-class.
- This pattern takes out the responsibility of the instantiation of a class from the client program to the factory class.

> [!Note]   
> This pattern is also known as Factory Method Design Pattern.

> [!Tip]   
> Use the Factory Method when you want to save system resources by reusing existing objects instead of rebuilding them each time.   
> Use the Factory Method when you want to provide users of your library or framework with a way to extend its internal components.  
> Use the Factory Method when you don’t know beforehand the exact types and dependencies of the objects your code should work with. 


- Super class in factory design pattern can be an <u>interface</u>, <u>abstract class</u> or a <u>normal java class</u>.

- Here is an example for it:

    ```java

    //Abstract Super Class

    public abstract class Computer {
    
    	public abstract String getRAM();
    	public abstract String getHDD();
    	public abstract String getCPU();
    
    	@Override
    	public String toString(){
    		return "RAM= "+this.getRAM()+", HDD="+this.getHDD()+", CPU="+this.getCPU();
    	}
    }

    ```

    ```java
    
    //Sub Class PC
    
    public class PC extends Computer {

	    private String ram;
	    private String hdd;
	    private String cpu;
    
	    public PC(String ram, String hdd, String cpu){
	    	this.ram=ram;
	    	this.hdd=hdd;
	    	this.cpu=cpu;
	    }
	    @Override
	    public String getRAM() {
	    	return this.ram;
	    }

	    @Override
	    public String getHDD() {
	    	return this.hdd;
	    }

	    @Override
	    public String getCPU() {
	    	return this.cpu;
	    }

    }
    
    ```
    ```java
    
    //Sub Class Server

    public class Server extends Computer {

    	private String ram;
    	private String hdd;
    	private String cpu;
    
    	public Server(String ram, String hdd, String cpu){
    		this.ram=ram;
    		this.hdd=hdd;
    		this.cpu=cpu;
    	}
    	@Override
    	public String getRAM() {
    		return this.ram;
    	}

    	@Override
    	public String getHDD() {
    		return this.hdd;
    	}

    	@Override
    	public String getCPU() {
    		return this.cpu;
    	}

    }
    
    ```
    ```java
    //Factory Class

    public class ComputerFactory {

    	public static Computer getComputer(String type, String ram, String hdd, String cpu){
    		if("PC".equalsIgnoreCase(type)){
                return new PC(ram, hdd, cpu);
            } 
    		else if("Server".equalsIgnoreCase(type)) {
                return new Server(ram, hdd, cpu);
            }
    
    		return null;
    	}
    }

    ```

## Factory Design Pattern Perks

- Factory design pattern provides approach to code for interface rather than implementation.   
- Factory pattern removes the instantiation of actual implementation classes from client code. Factory pattern makes our code more robust, less coupled and easy to extend. For example, we can easily change PC class implementation because client program is unaware of this.   
- Factory pattern provides abstraction between implementation and client classes through inheritance.  

- `Single Responsibility Principle`. You can move the product creation code into one place in the program, making the code easier to support.
- `Open/Closed Principle`. You can introduce new types of products into the program without breaking existing client code.

## Factory Design Pattern Drawbacks

- The code may become more complicated since you need to introduce a lot of new subclasses to implement the pattern. The best case scenario is when you’re introducing the pattern into an existing hierarchy of creator classes.