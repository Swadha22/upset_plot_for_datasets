### upset plot for all the datasets

  setwd('~/Desktop')
  install.packages("UpSetR")
  library(UpSetR)

  # reading the filtered gene list file…
  
  HTAS<-read.csv("Gene_list.csv")
  
  head(HTAS)

#### selecting the genes from each replicate
  
  myList <- list(
    'HTAS.C.S39'= HTAS$HTAS.C.S39.ChIP,
    'HTAS.C.S41'= HTAS$HTAS.C.S41.ChIP,
    'HTAS.N.S41'= HTAS$HTAS.N.S41.ChIP)



  listInput <- list('HTAS.C.S39' = unlist(myList[['HTAS.C.S39']], use.names = FALSE),
                    'HTAS.C.S41' = unlist(myList[['HTAS.C.S41']], use.names = FALSE),
                    'HTAS.N.S41' = unlist(myList[['HTAS.N.S41']], use.names =FALSE))
                    
                    

  upset(fromList(listInput),
        order.by = 'freq',
        text.scale = 1.5,
        set_size.show = TRUE,
        set_size.scale_max = 7000)
        
        
