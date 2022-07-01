 function SignalGen()
answer1 = inputdlg(' Enter the sampling frequency','Sampling Frequency',[1 50]);
fs = str2num(answer1{1});
answer2 = inputdlg(' Enter The start and end of time scale(space-separated)', 'Time scale', [1,50]);
ts=str2num(answer2{1});
answer3 = inputdlg('Enter the number of breakpoints','Breakpoints number',[1 50]);
bp= str2num(answer3{1});
position (1,1)=ts(1);
if bp==0
    time=ts(2)-ts(1);
x=time*fs;
t=linspace(ts(1),ts(2),x);
str = [ 'Signal:'];
X=[];
choice=menu(str,'DC','Ramp','General Order Polonomyal ' , 'Exponential' , 'Sinosoidal');
if choice == 1 
    dlgtitleDC = 'DC';
    promptDC = {'Amplitude :'};
    definput = {'0'}; 
    answer = inputdlg(promptDC,dlgtitleDC,[1 50],definput);
    amplitudeDC=str2num(answer{1});
     X=amplitudeDC*ones(1,x);
     plot(t,X)
end
if choice == 2 
    dlgtitleRAMP = 'Ramp';
    promptRAMP = {'Slope :' , 'Intercept :' };
    definput={'0','0'};
    answer = inputdlg(promptRAMP,dlgtitleRAMP,[1 50],definput);
    slopeRAMP=str2num(answer{1});
    interceptRAMP=str2num(answer{2});
      X=(slopeRAMP*t)+interceptRAMP;
      plot(t,X)
end
    if choice == 3
    dlgtitleGOE = 'General Order Polonomyal ';
    promptGOE = { 'Intercept' , ' Power :'  };
    definput={'0','0'};
    answer = inputdlg(promptGOE,dlgtitleGOE,[1 50],definput);
    powerGOE=str2num(answer{2});
    interceptGOE=str2num(answer{1});
  
    %  for k =1 : powerGOE+1
  %   dlgtitleCOF = 'General Order Polonomyal ';
    % promptCOF= ['Coefficiant of x to the power  ' num2str( powerGOE - k +1 ) ':'] ;
    % answer = inputdlg(promptCOF,dlgtitleCOF,[1 50],definput);
    % Coeff(1,k)= str2num(answer{1});
     
     % end
         %X=amplitudeGOE*polyval(Coeff,t);
         X=(powerGOE.^t+interceptGOE);
         plot(t,X)

    end
     if choice == 4 
    dlgtitleEXPO = 'Exponential';
    promptEXPO = {'Amplitude :' ,'Exponent :' };
    definput={'0','0'};
    answer = inputdlg(promptEXPO,dlgtitleEXPO,[1 50],definput);
    amplitudeEXPO=str2num(answer{1});
    exponenttEXPO=str2num(answer{2});
    X=amplitudeEXPO*(exp(t.^exponenttEXPO));
    plot(t,X)
    end
    if choice == 5
    dlgtitleSIN = 'Sinsoidal ';
    promptSIN = {'Amplitude :' , 'Frequency'  , 'Intercept :' };
    definput={'0','0','0'};
    answer = inputdlg(promptSIN,dlgtitleSIN,[1 50],definput);
    amplitudeSIN=str2num(answer{1});
    frequencySIN=str2num(answer{2});
    phaseSIN=str2num(answer{3});
    X=amplitudeSIN*sin(2*pi*frequencySIN*t+ phaseSIN);
    plot(t,X)
    end
end
    if bp >0
   
for i = 1:bp
    promptnb = { [ 'Position ' num2str(i) ':']};
    definput = {'0'}; 
    answer = inputdlg(promptnb);
    position(1,i+1) = str2num(answer{1});
end
position(1,bp+2) = ts(2) ;
i=1;
time=ts(2)-ts(1);
x=time*fs;
t=linspace(ts(1),ts(2),x); X=[];

for i = 1:bp+1
    if position(1,i)== ts(2)
        break;
    else
    str = [ 'Signal  ' num2str(i) ':'];
    choice(1,i)=menu(str,'DC','Ramp','General Order Polonomyal ' , 'Exponential' , 'Sinosoidal');
if choice(1,i) == 1 
    dlgtitleDC = 'DC';
    promptDC = {'Amplitude :'};
    definput = {'0'}; 
    answer = inputdlg(promptDC,dlgtitleDC,[1 40],definput);
    amplitudeDC(1,i)=str2num(answer{1});
    X1=  amplitudeDC(1,i)*ones(1,((position(1,i+1)-position(1,i))*fs));
    X2 = 0;
     end
     if choice(1,i) == 2 
    dlgtitleRAMP = 'Ramp';
    promptRAMP = {'Slope :' , 'Intercept :' };
    definput={'0','0'};
    answer = inputdlg(promptRAMP,dlgtitleRAMP,[1 50],definput);
    slopeRAMP(1,i)=str2num(answer{1});
    interceptRAMP(1,i)=str2num(answer{2});
    x= (position(1,i+1)-position(1,i)).*fs;
    t1=linspace(position(1,i), position(1,i+1),x);
    X1=slopeRAMP(1,i)*t1 + interceptRAMP(1,i) ;
    end
    if choice(1,i) == 3
    dlgtitleGOE = 'General Order Polonomyal ';
    promptGOE = { 'Amplitude' , ' Power :'  };
    definput={'0','0'};
    answer = inputdlg(promptGOE,dlgtitleGOE,[1 50],definput);
    powerGOE(1,i)=str2num(answer{2});
    amplitudeGOE(1,i)=str2num(answer{1});
    t1=linspace(position(1,i) , position(1,i+1),((position(1,i+1)- position(1,i))*fs));
    for k =1 : powerGOE(1,i)+1
     dlgtitleCOF = 'General Order Polonomyal ';
     promptCOF= ['Coefficiant of x to the power  ' num2str( powerGOE(1,i) - k +1 ) ':'] ;
     answer = inputdlg(promptCOF,dlgtitleCOF,[1 50],definput);
     Coeff(1,k)= str2num(answer{1});
     
    end
    X1=amplitudeGOE(1,i)*polyval(Coeff,t1);

    end
    if choice(1,i) == 4 
    dlgtitleEXPO = 'Exponential';
    promptEXPO = {'Amplitude :' ,'Exponent :' };
    definput={'0','0'};
    answer = inputdlg(promptEXPO,dlgtitleEXPO,[1 50],definput);
    amplitudeEXPO(1,i)=str2num(answer{1});
    exponenttEXPO(1,i)=str2num(answer{2});
    t1=linspace(position(1,i) , position(1,i+1),((position(1,i+1)-position(1,i))*fs));
    X1=  amplitudeEXPO(1,i)*(exp(t1.^exponenttEXPO(1,i)));
    end
    if choice(1,i) == 5
    dlgtitleSIN = 'Sinsoidal ';
    promptSIN = {'Amplitude :' , 'Frequency'  , 'Intercept :' };
    definput={'0','0','0'};
    answer = inputdlg(promptSIN,dlgtitleSIN,[1 50],definput);
    amplitudeSIN(1,i)=str2num(answer{1});
    frequencySIN(1,i)=str2num(answer{2});
    phaseSIN(1,i)=str2num(answer{3});
    t1=linspace(position(1,i) , position(1,i+1),((position(1,i+1)-position(1,i))*fs));
    X1=amplitudeSIN(1,i)*sin(2*pi*frequencySIN(1,i)*t1+ phaseSIN(1,i));
    
    
    end
    X=[X X1];
    end
end
plot(t,X)
ylim([-10 10])
xlim([-10 10])
grid on

     answer10= inputdlg('Do you want to perform any operations for the resulted signal? answer with 1 if YES and with 0 if NO','Operations on signal',[1 100]);
     s= str2num(answer10{1});
     if s==0
         return
     elseif s==1
         z=menu(str,'Amplitude Scaling','Time shift','Expanding the signal '  , 'Compressing the signal');         
      if z==1
    answer12= inputdlg('Enter the scale value','Amp scale',[1 50]);
    A1= str2num(answer12{1});
    y2=A1.*X;
    plot(t,y2)
         elseif z==2 
       
             answer12 = inputdlg('Enter the shift value','time shift',[1 50]);
             tshift= str2num(answer12{1});
             if key==4
                 y2= X.*exp(ts);
                 plot(t,y2)
             else
             t2=t-tshift;
             plot(t2,X)
             end
         elseif z==3
             answer12 = inputdlg('Enter the expansion value','time shift',[1 50]);
             tshift= str2num(answer12{1});
             
             if choice==4
                 y2=  amplitudeEXPO*exp(tshift.*log(X/amplitudeEXPO));
                 plot(t,y2)
             else
             t2=t.*tshift;
             plot(t2,X)
             end
         elseif z==4
             answer12 = inputdlg('Enter the compression value','time shift',[1 50]);
             tshift= str2num(answer12{1});
             if choice==4
                 y2= amplitudeEXPO*exp(log(X/amplitudeEXPO)./tshift);
                 plot(t,y2)
             else
             t2=t./tshift;
             plot(t2,X)
             end 
         end
     end
end
