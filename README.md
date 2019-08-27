# utl-transpose-macro-rather-than-proc-print-report-or-tabulate
Transpose macro rather than proc print report or tabulate 
    SAS Forum: Transpose macro rather than proc print report or tabulate                                                          
                                                                                                                                  
    SOAPBOX ON                                                                                                                    
    SAS transpose cannot easily transpose multiple sets of variables.                                                              
    Arts flexible and very fast transpose macro is perfect for this problem.                                                      
    The benefit of the transpose macro is an output dataset structured like the report.                                           
    With Arts macro programmers are much less likely to be paintd into a corner.                                                  
    SOAPBOX OFF                                                                                                                   
                                                                                                                                  
     github                                                                                                                       
    https://tinyurl.com/y4uj2m2m                                                                                                  
    https://github.com/rogerjdeangelis/utl-transpose-macro-rather-than-proc-print-report-or-tabulate                              
                                                                                                                                  
    SAS Forum                                                                                                                     
    https://tinyurl.com/y3wog7tm                                                                                                  
    https://communities.sas.com/t5/SAS-Procedures/proc-report-or-proc-tabulate-to-create-a-report-of-a-sas-dataset/m-p/584121     
                                                                                                                                  
    macros                                                                                                                        
    https://tinyurl.com/y9nfugth                                                                                                  
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories                                    
                                                                                                                                  
    other transpose repos(52)                                                                                                     
    https://github.com/rogerjdeangelis?utf8=%E2%9C%93&tab=repositories&q=transpose+in%3Aname&type=&language=                      
                                                                                                                                  
    *_                   _                                                                                                        
    (_)_ __  _ __  _   _| |_                                                                                                      
    | | '_ \| '_ \| | | | __|                                                                                                     
    | | | | | |_) | |_| | |_                                                                                                      
    |_|_| |_| .__/ \__,_|\__|                                                                                                     
            |_|                                                                                                                   
    ;                                                                                                                             
                                                                                                                                  
    data have;                                                                                                                    
     input YOA Lvl $ Val Ult;                                                                                                     
    cards4;                                                                                                                       
    2000 First 23 67                                                                                                              
    2001 First 54 58                                                                                                              
    2002 First 567 34                                                                                                             
    2000 second 34 46                                                                                                             
    2001 second 34 46                                                                                                             
    2002 second 56 97                                                                                                             
    2000 third 54 32                                                                                                              
    2001 third 68 13                                                                                                              
    2002 third 45 98                                                                                                              
    ;;;;                                                                                                                          
    run;quit;                                                                                                                     
                                                                                                                                  
    WORK.HAVE total obs=9                                                                                                         
                                                                                                                                  
      YOA     LVL      VAL    ULT                                                                                                 
                                                                                                                                  
     2000    First      23     67                                                                                                 
     2001    First      54     58                                                                                                 
     2002    First     567     34                                                                                                 
     2000    second     34     46                                                                                                 
     2001    second     34     46                                                                                                 
     2002    second     56     97                                                                                                 
     2000    third      54     32                                                                                                 
     2001    third      68     13                                                                                                 
     2002    third      45     98                                                                                                 
                                                                                                                                  
    *            _               _                                                                                                
      ___  _   _| |_ _ __  _   _| |_                                                                                              
     / _ \| | | | __| '_ \| | | | __|                                                                                             
    | (_) | |_| | |_| |_) | |_| | |_                                                                                              
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                             
                    |_|                                                                                                           
    ;                                                                                                                             
                                                                                                                                  
     RULES            Pair one           Pair two          Pair three                                                             
                   ==============    ================    ==============                                                           
                                                                                                                                  
                                                                                                                                  
    WORK.WANT total obs=3                                                                                                         
                                                                                                                                  
                    VAL_     ULT_     VAL_      ULT_      VAL_     ULT_                                                           
    Obs     YOA    FIRST    FIRST    SECOND    SECOND    THIRD    THIRD                                                           
                                                                                                                                  
     1     2000      23       67       34        46        54       32                                                            
     2     2001      54       58       34        46        68       13                                                            
     3     2002     567       34       56        97        45       98                                                            
                                                                                                                                  
    *                                                                                                                             
     _ __  _ __ ___   ___ ___  ___ ___                                                                                            
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|                                                                                           
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                                           
    | .__/|_|  \___/ \___\___||___/___/                                                                                           
    |_|                                                                                                                           
    ;                                                                                                                             
                                                                                                                                  
    %utl_transpose(data=have, out=want, by=yoa, id=lvl, delimiter=_, var=val ult,sort=yes);                                       
                                                                                                                                  
    proc print data=want;                                                                                                         
    run;quit;                                                                                                                     
                                                                                                                                  
                                                                                                                                  
