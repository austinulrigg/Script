#####Read Data From Text File#####
Dataset <- readXL("C:/Users/austi/Downloads/Data_TaxEvaders.xlsx", rownames=FALSE, header=TRUE, na="", sheet="Sheet2", stringsAsFactors=TRUE)
#####Linear regression#####
library(aod, pos=18)
RegModel.1 <- lm(HoursRadio~Hours.TV., data=Dataset)
res <- NULL
(res <- summary(RegModel.1))
vif(RegModel.1)
###variance inflation factors
multireg.table <- NULL
multireg.table <- cbind(res$coefficients[,1], confint(RegModel.1),res$coefficients[,2:4])
colnames(multireg.table)[1] <- "Estimate"
colnames(multireg.table) <- gettext(domain="R-RcmdrPlugin.EZR", colnames(multireg.table))
multireg.table
