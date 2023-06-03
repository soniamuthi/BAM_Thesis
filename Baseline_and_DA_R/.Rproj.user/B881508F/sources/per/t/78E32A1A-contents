library(readr)
library(dplyr)
library(lme4)
library(stringr)
library(lmerTest)
library(domir)
library(relaimpo)
library(MuMIn)
library(stargazer)
library(rsq)

df_position <- read_csv("df_position.csv")
df_positions <- df_position[,-1]

df_positions$TeamName <- as.factor(df_positions$TeamName)
df_positions$raceID <- as.factor(df_positions$raceID)
df_positions$CircuitType <- as.factor(df_positions$CircuitType)
df_positions$Engine <- as.factor(df_positions$Engine)
df_positions$Rain <- as.numeric(df_positions$Rain)

df_positions <- df_positions[,-1]
df_positions <- df_positions[,-4]

df_positions$GridPosition[df_positions$GridPosition == 0] <- 20

df_0_try <- subset(df_positions, Year %in% c(2019, 2020))
df_1_try <- subset(df_positions, Year %in% c(2021, 2022))

df_0_try  <- df_0_try [,-4]
df_1_try  <- df_1_try [,-4]


# Dominance Analysis

# specify categories
driver <- c('GridPosition' ,' AverageSpeed'  , 'AverageThrottle' , 'Brake' , 'driverIssue', "AgeAtGP", 'SDLapTime', 'BestQualiTime', 'MaxThrottlePct')
car <- c('MaxRPM' , 'carIssue' , 'TeamName' , 'AvgPitTime' , 'PitstopNo', 'Engine', 'HARD', 'INTERMEDIATE', 'MEDIUM', 'SOFT', 'WET', 'MaxSpeed')
other <- c("CircuitType", 'Rain')

# DA
domin(Position ~ 1, 
      lmer, 
      list(\(x) list(R2m = MuMIn::r.squaredGLMM(x)[[1]]), "R2m"), 
      data = df_0_try, 
      sets = list(driver,car, other),
      consmodel = "(1 | raceID)")

domin(Position ~ 1, 
      lmer, 
      list(\(x) list(R2m = MuMIn::r.squaredGLMM(x)[[1]]), "R2m"), 
      data = df_1_try, 
      sets = list(driver,car, other),
      consmodel = "(1 | raceID)")


# subcategories
demo <- c("AgeAtGP")
quali  <- c('GridPosition' ,'BestQualiTime')
raceperf  <- c( 'AverageSpeed'  , 'AverageThrottle' , 'Brake' , 'driverIssue', 'SDLapTime', 'MaxThrottlePct')
team <- c( 'TeamName')
strategy <- c('AvgPitTime' , 'PitstopNo', 'HARD', 'INTERMEDIATE', 'MEDIUM', 'SOFT', 'WET')
technical <- c('MaxRPM' , 'carIssue' ,  'Engine', 'MaxSpeed')
other <- c('Rain', 'CircuitType')

# DA
domin(Position ~ 1, 
      lmer, 
      list(\(x) list(R2m = MuMIn::r.squaredGLMM(x)[[1]]), "R2m"), 
      data = df_0_try, 
      sets = list(demo,quali,raceperf,team,strategy,technical,other),
      consmodel = "(1 | raceID)")

domin(Position ~ 1, 
      lmer, 
      list(\(x) list(R2m = MuMIn::r.squaredGLMM(x)[[1]]), "R2m"), 
      data = df_1_try, 
      sets = list(demo,quali,raceperf,team,strategy,technical, other),
      consmodel = "(1 | raceID)")



# Baseline models

model_before <- lmer(Position ~ GridPosition + FLap + AverageSpeed +  
                AverageThrottle + Brake + driverIssue + SDLapTime + AvgPitTime + PitstopNo + MaxRPM + carIssue + TeamName + Engine + HARD + INTERMEDIATE + MEDIUM + SOFT + (1|raceID), data = df_0_try)


model_after <- lmer(Position ~ GridPosition + FLap + AverageSpeed +  
                AverageThrottle + Brake + driverIssue + SDLapTime + AvgPitTime + PitstopNo + MaxRPM + carIssue + TeamName + Engine + HARD + INTERMEDIATE + MEDIUM + SOFT + (1|raceID), data = df_1_try)

# R2
r.squaredGLMM(model_before, rft = "marginal")
r.squaredGLMM(model_after, rft = "marginal")

# Generate stargazer table
class(model_before) <- "lmerMod"
class(model_after) <- "lmerMod"

stargazer(model_before, model_after, type = "latex", font.size = 'small', column.sep.width = "1pt", single.row = TRUE)


# Robustness check

df_points <- read_csv("df_points.csv")
df_points <- df_points[,-1]

df_points$GridPosition[df_points$GridPosition == 0] <- 20

df_points$TeamName <- as.factor(df_points$TeamName)
df_points$raceID <- as.factor(df_points$raceID)
df_points$CircuitType <- as.factor(df_points$CircuitType)
df_points$Engine <- as.factor(df_points$Engine)
df_points$Rain <- as.numeric(df_points$Rain)

df_points <- df_points[,-1]
df_points <- df_points[,-4]

df_0_try <- subset(df_points, Year %in% c(2019, 2020))
df_1_try <- subset(df_points, Year %in% c(2021, 2022))



model_before <- lmer(Points ~ GridPosition + FLap + AverageSpeed +  
                       AverageThrottle + Brake + driverIssue + SDLapTime + AvgPitTime + PitstopNo + MaxRPM + carIssue + TeamName + Engine + HARD + INTERMEDIATE + MEDIUM + SOFT + (1|raceID), data = df_0_try)

model_after <- lmer(Points ~ GridPosition + FLap + AverageSpeed +  
                      AverageThrottle + Brake + driverIssue + SDLapTime + AvgPitTime + PitstopNo + MaxRPM + carIssue + TeamName + Engine + HARD + INTERMEDIATE + MEDIUM + SOFT + (1|raceID), data = df_1_try)


r.squaredGLMM(model_before, rft = "marginal")
r.squaredGLMM(model_after, rft = "marginal")


stargazer(model_before, model_after, type = "latex", single.row = TRUE, column.sep.width = "1pt")

# DA
domin(Points ~ 1, 
      lmer, 
      list(\(x) list(R2m = MuMIn::r.squaredGLMM(x)[[1]]), "R2m"), 
      data = df_0_try, 
      sets = list(driver,car, other),
      consmodel = "(1 | raceID)")

domin(Points ~ 1, 
      lmer, 
      list(\(x) list(R2m = MuMIn::r.squaredGLMM(x)[[1]]), "R2m"), 
      data = df_1_try, 
      sets = list(driver,car, other),
      consmodel = "(1 | raceID)")
