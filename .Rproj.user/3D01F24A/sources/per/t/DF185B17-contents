###
library(dplyr)

WorldView <- setClass("WorldView",
                       slots = c(
                         edges = "tbl",
                         nodes = "tbl",
                         envir = "environment",
                         iter = "list",
                         models = "tbl"
                       ))

setMethod(
  f = "initialize",
  signature = "WorldView",
  definition = function(.Object)
  {
    .Object@nodes <- tibble(
      id = numeric(),
      name = character(),
      modelPredict = character(),
      modelUpdate = character(),
      modelErrorFunc = character()
    )
    .Object@edges <- tibble(
      sourceId = character(),
      sinkId = character()
    )

    .Object@iter <- tibble(
      num = numeric(),
      actualData = character(),
      prediction = character(),
      error = numeric()
    )

    .Object@model <- tibble(
      name = character(),
      func = character()
    )

    Object@models <-  Object@models %>% dplyr::add_row(name = "rand", func = "sample")
    Object@models <-  Object@models %>% dplyr::add_row(name = "rand", func = "sum")
    Object@models <-  Object@models %>% dplyr::add_row(name = "rand", func = "diff")

    .Object@envir <- new.env()
    return(.Object)
  }
)

setGeneric(
  name = "train",
  def = function(object, data)
  {
    standardGeneric("train")
  }
)

.train = function(object, data){
 # Check if graph exists
  if(nrow(object@nodes) == 0){
    randInd <- sample(1:nrow(object@models), 1)
    nodeToAdd <- dplyr::filter(row_number() == randInd)
    dplyr::rbind_all(object@nodes, nodeToAdd)
    # check if accuracy is increasing over iterations
  }else{

  }
  # If yes, score the graph, calulate error, update all principles
  # If no, spawn a new principle with a random function and add it to graph based on data

}

