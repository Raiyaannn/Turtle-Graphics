# Turtle-Graphics
package ttlgrphcs;

import java.awt.Color;

import java.awt.FlowLayout;

import javax.swing.JFrame;

import uk.ac.leedsbeckett.oop.LBUGraphics;

import javax.swing.JOptionPane;

import javax.imageio.ImageIO;

import java.io.File;

import java.io.IOException;

import java.awt.image.BufferedImage;



public class GraphicsSystem extends LBUGraphics
{
	public int data = 0;
/**
	 * 
	 */
	private static final long serialVersionUID = 1L;
		public static void main(String[] args)
        {
                new GraphicsSystem(); 
                
        }
				
        
		public void RGB(int Vred, int Vgreen, int Vblue) {
			Color rgbcolor = new Color(Vred, Vgreen, Vblue);
			setPenColour(rgbcolor);
		}
		
		
        public GraphicsSystem()
        
        {
                JFrame MainFrame = new JFrame("Raiyan Ibn Farid - TurtleGraphics");                
                MainFrame.setLayout(new FlowLayout());  
                MainFrame.add(this);                                   
                MainFrame.pack();                                               
                MainFrame.setVisible(true);
                setBackground_Col(Color.BLACK);
                displayMessage("Raiyan Ibn Farid"); 
                about();
                
        }
    
        public String allCommands(String CommandCheck) 
        {
     	   String[] allCommands = { "penup","pendown", "turnright", "turnleft", "forward", "backward", "about", "black", "green", "red", "white", "blue", "pink", "yellow", "purple", "rgb", "reset", "clear", "load", "save", "savecommand", "loadcommand", "pencolor", "square", "circle", "triangle" };
     	   
     	   for (String Check:allCommands) 
     	   { 
     		  if (Check.equals(CommandCheck))
     			  return Check;
     	   }
     	   return"";
     	   
     	   
        }
         
    	@Override
    	 public void about() {
            super.about(); 

            
            String Name = "Raiyan"; 
            String message = "Edited: " + Name;
            displayMessage(message);
        }

    	
    	
	@Override
	public void processCommand(String commandWorks) 
	{
		
		String[] Works = commandWorks.split(" ");
		String CommandCheck = allCommands(Works[0]);
		
		int parameter = 0;
		
		
		if(Works.length>1) {
			parameter = -1;
			
			try
			{
				parameter = Integer.parseInt(Works[1]); //converting string into integer.
				
				
			}
			catch (Exception Errors) 
			{
				JOptionPane.showMessageDialog(null, "Error: An invalid command has been entered");
				parameter = -2;
			}
			
			
			
		}
		
		
		switch(CommandCheck) 
		{
		case "penup":
			if (parameter !=0)
			{
				JOptionPane.showMessageDialog(null, "Error: Cannot enter a parameter.");
				
			}
			else 
			{
				penUp();
				data = 0;
			}
			break;
			
		case "pendown":
			if (parameter !=0) 
			{
				JOptionPane.showMessageDialog(null, "Error: Cannot enter a parameter.");
				
			}
			else 
			{
				penDown();
				data = 0;
			}
			break;
			
		case "turnright":
			if (parameter == 0) 
			{
				
				turnRight(parameter);
				
			}
			else 
			{
				turnRight(90);
				data = 0;
			}
			break;
			
		case "turnleft":
			if (parameter == 0) 
			{
				turnLeft(90);
				
			}
			else 
			{
				turnLeft(parameter);
				data = 0;
			}
			break;
			
		case "forward":
			if (parameter == 0) 
			{
				forward(100);
				
			}
			else 
			{
				forward(parameter);
				data = 0;
				
			}
			break;
			
		case "backward":
			if (parameter == 0) 
			{
				forward(-100);
				
			}
			else 
			{
				forward(parameter*-1);
				data = 0;
			}
			break;
			
		case "about":
            about();
            data = 0;
            break;
			
		case "black":
			if (parameter != 0) 
			{
				JOptionPane.showMessageDialog(null, "Error: Colors can not be defined as numbers");
				
			}
			else 
			{
            setPenColour(Color.BLACK);
            data = 0;
            break;
            }
            
		case "green":
			if (parameter != 0) 
			{
				JOptionPane.showMessageDialog(null, "Error: Colors can not be defined as numbers");
				
			}
			else 
			{
            setPenColour(Color.GREEN);
            data = 0;
            break;
            }
            
            
		case "red":
			if (parameter != 0) 
			{
				JOptionPane.showMessageDialog(null, "Error: Colors can not be defined as numbers");
				
			}
			else 
			{
            setPenColour(Color.RED);
            data = 0;
            break;
            }
            
		case "white":
			if (parameter != 0) 
			{
				JOptionPane.showMessageDialog(null, "Error: Colors can not be defined as numbers");
				
			}
			else 
			{
            setPenColour(Color.WHITE);
            data = 0;
            break;
            }
            
		case "blue":
			if (parameter != 0) 
			{
				JOptionPane.showMessageDialog(null, "Error: Colors can not be defined as numbers");
				
			}
			else 
			{
            setPenColour(Color.BLUE);
            data = 0;
            break;
            }
            
		case "pink":
			if (parameter != 0) 
			{
				JOptionPane.showMessageDialog(null, "Error: Colors can not be defined as numbers");
				
			}
			else 
			{
            setPenColour(Color.PINK);
            data = 0;
            break;
            }
            
		case "purple":
			if (parameter != 0) 
			{
				JOptionPane.showMessageDialog(null, "Error: Colors can not be defined as numbers");
				
			}
			else 
			{
            setPenColour(new Color(128,0,128));
            data = 0;
            break;
            }
           
            
		case "yellow":
			if (parameter != 0) 
			{
				JOptionPane.showMessageDialog(null, "Error: Colors can not be defined as numbers");
				
			}
			else 
			{
            setPenColour(new Color(255,255,0));
            data = 0;
            break;
			}
			
		case "rgb":
			if (parameter == 0) 
			{
				JOptionPane.showMessageDialog(null, "Error: You must enter 3 parameters");
				
			}
			else {
			RGB(parameter, parameter, parameter);
			JOptionPane.showMessageDialog(null, "Color set successfully");
			}
			break;
			
			
           
            
		case "reset":
			data = 1;
			
			if (parameter != 0) 
			{
				JOptionPane.showMessageDialog(null, "Error: Invalid command");
				
			}
			else 
			{
				reset();
				data = 0;
	            
			}
            break;
            
            
		case "clear":
			data = 1;
			
            clear();
            data = 0;
            break;
            
            
        case "load":
			
		    if (parameter != 0) {
		        JOptionPane.showMessageDialog(null, "Error: Invalid command");
		    } else {
		        if (data == 1) {
		            BufferedImage LoadImg = null;
		            try {
		                LoadImg = ImageIO.read(new File("TurteSave.png"));
		                JOptionPane.showMessageDialog(null, "Loaded successfully");
		            } catch (IOException exp) {}
		            setBufferedImage(LoadImg);
		        } else {
		            JOptionPane.showMessageDialog(null, "You must save the image first");
		        }
		    }
		    break;
		    
		    
		case "save":
			
			if(parameter != 0 ) 
			{
				JOptionPane.showMessageDialog(null, "Error: Invalid command");
			}
			else 
			{
				BufferedImage img = getBufferedImage();
				File output = new File ("TurtleSave.png");
				try 
				{
					ImageIO.write(img, "png", output);
					data = 1;
					JOptionPane.showMessageDialog(null, "Successfully saved image");
					
				}
				catch (IOException exception)
				{}
				
				
			}
            break;
        
            
		case "square":
			if (parameter == 0) 
			{
				JOptionPane.showMessageDialog(null, "Error: No parameters has been entered.");
				
			}
			else 
			{
				
			     for (int i = 0; i < 4; i++) 
			     {
			    	 forward(parameter);
			    	 this.turnLeft(90);
			     }
			     this.reset();
			     break;
			
			}
			
		case "triangle":
			if (parameter == 0) 
			{
				JOptionPane.showMessageDialog(null, "Error: No parameters has been entered.");
				
			}
			else
			{
				for (int i = 0; i < 3; i++) 
			     {
					 
					 forward(parameter);
			    	 this.turnLeft(120);
			     }
			     this.reset();
			     break;
			     }
			     
			case "circle":
				if (parameter == 0) 
				{
					JOptionPane.showMessageDialog(null, "Error: Must enter radius");
					
				}
				else
				{
					circle(parameter);
					break;
					
					
			     
		 
			
				
			}
			
		case "speed":
			if (parameter == 0) 
			{
				JOptionPane.showMessageDialog(null, "Error: No parameters has been entered.");
				
			}
			else
			{
				setTurtleSpeed(parameter);
			
			}
			break;
			
	 
      default:
       JOptionPane.showMessageDialog(null, "Error: Invalid command");
       break;
		}
	}
}
		
		
		
	
       

        
        
       
                            
                            
                            
                       
                        
                        
                       
                
                
                
        
        
        
        	
        	
		
        
		
			
			
			
				
			
			
		


			
			
	


