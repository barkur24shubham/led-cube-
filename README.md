LED CUBE PROJECT CREATED ON 20/07/2017
*******************************************************/

#include <mega8.h>

#include <delay.h>



void main(void)
{
    int i,j,k,D; 
DDRB=(1<<DDB7) | (1<<DDB6) | (1<<DDB5) | (1<<DDB4) | (1<<DDB3) | (1<<DDB2) | (1<<DDB1) | (1<<DDB0);
// State: Bit7=0 Bit6=0 Bit5=0 Bit4=0 Bit3=0 Bit2=0 Bit1=0 Bit0=0 
PORTB=(0<<PORTB7) | (0<<PORTB6) | (0<<PORTB5) | (0<<PORTB4) | (0<<PORTB3) | (0<<PORTB2) | (0<<PORTB1) | (0<<PORTB0);

// Port C initialization
// Function: Bit6=In Bit5=In Bit4=In Bit3=Out Bit2=Out Bit1=Out Bit0=Out 
DDRC=(0<<DDC6) | (0<<DDC5) | (0<<DDC4) | (1<<DDC3) | (1<<DDC2) | (1<<DDC1) | (1<<DDC0);
// State: Bit6=T Bit5=T Bit4=T Bit3=0 Bit2=0 Bit1=0 Bit0=0 
PORTC=(0<<PORTC6) | (0<<PORTC5) | (0<<PORTC4) | (0<<PORTC3) | (0<<PORTC2) | (0<<PORTC1) | (0<<PORTC0);

// Port D initialization
// Function: Bit7=Out Bit6=Out Bit5=Out Bit4=Out Bit3=Out Bit2=Out Bit1=Out Bit0=Out 
DDRD=(1<<DDD7) | (1<<DDD6) | (1<<DDD5) | (1<<DDD4) | (1<<DDD3) | (1<<DDD2) | (1<<DDD1) | (1<<DDD0);
// State: Bit7=0 Bit6=0 Bit5=0 Bit4=0 Bit3=0 Bit2=0 Bit1=0 Bit0=0 
PORTD=(0<<PORTD7) | (0<<PORTD6) | (0<<PORTD5) | (0<<PORTD4) | (0<<PORTD3) | (0<<PORTD2) | (0<<PORTD1) | (0<<PORTD0);

// Timer/Counter 0 initialization
// Clock source: System Clock
// Clock value: Timer 0 Stopped
TCCR0=(0<<CS02) | (0<<CS01) | (0<<CS00);
TCNT0=0x00;

// Timer/Counter 1 initialization
// Clock source: System Clock
// Clock value: Timer1 Stopped
// Mode: Normal top=0xFFFF
// OC1A output: Disconnected
// OC1B output: Disconnected
// Noise Canceler: Off
// Input Capture on Falling Edge
// Timer1 Overflow Interrupt: Off
// Input Capture Interrupt: Off
// Compare A Match Interrupt: Off
// Compare B Match Interrupt: Off
TCCR1A=(0<<COM1A1) | (0<<COM1A0) | (0<<COM1B1) | (0<<COM1B0) | (0<<WGM11) | (0<<WGM10);
TCCR1B=(0<<ICNC1) | (0<<ICES1) | (0<<WGM13) | (0<<WGM12) | (0<<CS12) | (0<<CS11) | (0<<CS10);
TCNT1H=0x00;
TCNT1L=0x00;
ICR1H=0x00;
ICR1L=0x00;
OCR1AH=0x00;
OCR1AL=0x00;
OCR1BH=0x00;
OCR1BL=0x00;

// Timer/Counter 2 initialization
// Clock source: System Clock
// Clock value: Timer2 Stopped
// Mode: Normal top=0xFF
// OC2 output: Disconnected
ASSR=0<<AS2;
TCCR2=(0<<PWM2) | (0<<COM21) | (0<<COM20) | (0<<CTC2) | (0<<CS22) | (0<<CS21) | (0<<CS20);
TCNT2=0x00;
OCR2=0x00;

// Timer(s)/Counter(s) Interrupt(s) initialization
TIMSK=(0<<OCIE2) | (0<<TOIE2) | (0<<TICIE1) | (0<<OCIE1A) | (0<<OCIE1B) | (0<<TOIE1) | (0<<TOIE0);

// External Interrupt(s) initialization
// INT0: Off
// INT1: Off
MCUCR=(0<<ISC11) | (0<<ISC10) | (0<<ISC01) | (0<<ISC00);

// USART initialization
// USART disabled
UCSRB=(0<<RXCIE) | (0<<TXCIE) | (0<<UDRIE) | (0<<RXEN) | (0<<TXEN) | (0<<UCSZ2) | (0<<RXB8) | (0<<TXB8);

// Analog Comparator initialization
// Analog Comparator: Off
// The Analog Comparator's positive input is
// connected to the AIN0 pin
// The Analog Comparator's negative input is
// connected to the AIN1 pin
ACSR=(1<<ACD) | (0<<ACBG) | (0<<ACO) | (0<<ACI) | (0<<ACIE) | (0<<ACIC) | (0<<ACIS1) | (0<<ACIS0);
SFIOR=(0<<ACME);

// ADC initialization
// ADC disabled
ADCSRA=(0<<ADEN) | (0<<ADSC) | (0<<ADFR) | (0<<ADIF) | (0<<ADIE) | (0<<ADPS2) | (0<<ADPS1) | (0<<ADPS0);

// SPI initialization
// SPI disabled
SPCR=(0<<SPIE) | (0<<SPE) | (0<<DORD) | (0<<MSTR) | (0<<CPOL) | (0<<CPHA) | (0<<SPR1) | (0<<SPR0);

// TWI initialization
// TWI disabled
TWCR=(0<<TWEA) | (0<<TWSTA) | (0<<TWSTO) | (0<<TWEN) | (0<<TWIE);

while (1)
      {
      // Place your code here   
      
      for(k=0;k<20;k++)
      {    
            d=100;
           PORTC=0b00000000;
           PORTB=0b00001111;
           delay_ms(d);  
           PORTB=0b11110000; 
           delay_ms(d);
           PORTB=0b00000000;
           PORTD=0b00001111; 
           delay_ms(d);   
           PORTB=0b11110000; 
           delay_ms(d);    
           PORTB=0b00000000;
           delay_ms(d);
      }
         for(k=0;k<7;k++)
     {   
       //inner multiplexing  
       
      PORTB=0b00000000;
      PORTD=0b00000000;
      PORTC=0b11111111; 
      PORTB.0=1;   
      PORTC.3=0;
      delay_ms(200);  
      PORTB.0=0;
      PORTC.3=1;
      delay_ms(50);     
      
      
      
      for(i=0;i<200;i++) 
      {     PORTB=0b00110011;
            PORTC=0b11110011;
            delay_ms(1); 
            PORTB=0b00000000;
            PORTD=0b00000000;   
            PORTC=0b11111111;   
      }
      delay_ms(50); 
      for(j=0;j<100;j++)
      {          //middle
            PORTB=0b01010111;
            PORTD=0b00000111;   
            PORTC.1=0;
            PORTC.3=0; 
            delay_ms(1);
      
            PORTB=0b00000000;
            PORTD=0b00000000;   
            PORTC.1=1;
            PORTC.3=1; 
      
            PORTB=0b00000101;
            PORTD=0b00000101;   
            PORTC.2=0;
 
            delay_ms(1);
      
            PORTB=0b00000000;
            PORTD=0b00000000;   
            PORTC=0b11111111;
            delay_ms(1);
             
      }
      //outer 
      delay_ms(50);  
      for(j=0;j<200;j++)
      {
            PORTB=0b10011111;
            PORTD=0b11111001;   
            PORTC.0=0;
            PORTC.3=0; 
            delay_ms(1);        
      
      
            PORTB=0b00000000;
            PORTD=0b00000000;   
            PORTC.0=1;
            PORTC.3=1;
      
      
            PORTB=0b00001001;
            PORTD=0b10010000;   
            PORTC.1=0;
            PORTC.2=0;
      
        
            delay_ms(1);   
            PORTB=0b00000000;
            PORTD=0b00000000;   
            PORTC=0b11111111;  
            delay_ms(1); 
      } 
      delay_ms(50);
           

      }
      for(i=0;i<7;i++)
            {  
              D=300;
              PORTC=0b00000000;
              PORTB.0=1;
              PORTD.7=1;
              delay_ms(D);
              PORTB.0=0;
              PORTD.7=0;
          
              PORTB.1=1;
              PORTB.4=1;
              PORTD.3=1;
              PORTD.6=1; 
              delay_ms(D);
          
              PORTB.1=0;
              PORTB.4=0;
              PORTD.3=0;
              PORTD.6=0; 
       
      
              PORTD.0=1;
              PORTB.5=1;
              PORTB.2=1; 
              PORTB.7=1;
              PORTD.2=1;
              PORTD.5=1;
              delay_ms(D); 
              
              PORTD.0=0;
              PORTB.5=0;
              PORTB.2=0;
              PORTB.7=0;
              PORTD.2=0;
              PORTD.5=0;
               
                                                  
              
              PORTB.3=1;
              PORTB.6=1;
              PORTD.1=1;
              PORTD.4=1;
              delay_ms(D); 
              
              PORTB.3=0;
              PORTB.6=0;
              PORTD.1=0;
              PORTD.4=0;
              PORTC=0b11111111; 
                                                                                                                                                                                                                                
                       //COMPLETE
              
       }          
       
   PORTC=0b11111111;
   PORTD=0b00000000;  
   PORTB=0b00000000;                                                                                                                                                                                                                                                                                                     
   delay_ms(1000);
   for(i=0;i<20;i++)
     {  
              PORTC=0b00000000;
              PORTB.3=1;
              PORTB.6=1;
              PORTD.1=1;
              PORTD.4=1;
              delay_ms(100);
              PORTB.3=0;
              PORTB.6=0;
              PORTD.1=0;
              PORTD.4=0;      
                  
              PORTB.0=1;            
              PORTB.5=1;
              PORTD.2=1;
              PORTD.7=1;  
                             
              delay_ms(100);
              PORTB.0=0;
              PORTB.5=0;
              PORTD.2=0;
              PORTD.7=0; 
              PORTC=0b11111111; 
              
              PORTC=0b00000000;
              PORTB.3=1;
              PORTB.6=1;
              PORTD.1=1;
              PORTD.4=1;   
              delay_ms(100);
                
           }  
   
        PORTC=0b11111111;
        PORTD=0b00000000;  
        PORTB=0b00000000;                                                                                                                                                                                                                                                                                                     
        delay_ms(1000);
        for(j=0;j<20;j++)
        {
        
              PORTB=0b11111111; 
              PORTD=0b11111111; 
              PORTC=0b11111111; 
              PORTC.0=0;
              delay_ms(200);
              PORTC.0=1;
              PORTC.1=0; 
              
              delay_ms(200);
              PORTC.1=1;
              PORTC.2=0;
              
              delay_ms(200);
              PORTC.2=1;
              PORTC.3=0;
              
              delay_ms(200);
              PORTC.3=1;
              
              delay_ms(200);
              PORTC.3=0;
              
              delay_ms(200);
              PORTC.3=1;
              PORTC.2=0;
              
              delay_ms(200); 
              PORTC.2=1;
              PORTC.1=0;
              
              delay_ms(200); 
              PORTC.1=1; 
              PORTC.0=0;
              
              
              delay_ms(200);
              PORTC.0=1;
        
              
              delay_ms(200);
                     
        
        
        }
     
      PORTC=0b11111111;
        PORTD=0b00000000;  
        PORTB=0b00000000;                                                                                                                                                                                                                                                                                                     
        delay_ms(1000);
        for(j=0;j<8;j++)
       { 
                                      
       PORTD=0b11110000; 
       delay_ms(1000); 
       PORTD=0b00000000;
       PORTB.0=1;       
       PORTB.4=1; 
       PORTD.0=1; 
       PORTD.7=1;   
       delay_ms(1000); 
       PORTB.0=0;       
       PORTB.4=0; 
       PORTD.0=0; 
       PORTD.7=0;  
       PORTB=0b00001111; 
       delay_ms(1000);   
       PORTB=0b00000000; 
       PORTB.3=1;       
       PORTB.7=1; 
       PORTD.3=1; 
       PORTD.7=1;   
       delay_ms(1000);   
       
       PORTB.3=0;       
       PORTB.7=0; 
       PORTD.3=0; 
       PORTD.7=0;   
       delay_ms(1000); 
       
       
        
        
        }   
}

}


