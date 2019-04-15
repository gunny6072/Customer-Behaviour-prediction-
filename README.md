# Customer-Behaviour-prediction-

library(arules) 
  str(dataset)
 # find association rules with default settings
 
   rules <- apriori(dataset)

  inspect(rules)
dataset <- read.csv("bank1.csv")
 # rules with rhs containing "loan" only
rules <- apriori(dataset,parameter = list(minlen=2, supp=0.005, conf=0.8),appearance = list(rhs=c("loan=no", "loan=yes"),default="lhs"), control = list(verbose=F))
rules.sorted <- sort(rules, by="lift")
inspect(rules.sorted)

library(arulesViz)
plot(rules)
 plot(rules, method="graph", control=list(type="items"))
plot(rules, method="paracoord", control=list(reorder=TRUE))
 
