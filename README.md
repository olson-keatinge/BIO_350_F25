# BIO_350_F25

Starting our BOI350 assignments repo.

IC Assignment 1: Chapter 1 of Ecology Handbook
- making a difference equation

IC Assignment 2: Chapter 2 of Ecology Handbook
- We practised exponential growth models 
- created an algorithm to model the growth of duckweed population in a pond over time. 
- we used command import matplotlib


IC in class example 1
- Very similar to the duckweed population growth model activity 
- Think I had issues so redid something maybe

Logistic growth - 1 
- Created a logistic growth model to analyse the plant population growth over time
- We considered the carrying capacity of the population - the plateau of the graph model 
- I copied code from the exponential graph and modified it to fit the logistic model

IC in class example 2 
- We imported panda and a csv data set
- Used matplotlib to plot the data set on a graph. It was no very aesthetically pleasing so we used copilot to make adjustments based on what we wanted eg align x and y axis point 0 and change the colour of graoh etc. 
- We added a carrying capacity line after finding the averages between days 17 and 60 where the population undulated. then labelled it

IC in class example 3 - Lotka Volterra competition model ch 4 
- How to calculate and solve for the ability to coexist?
- Stability; 
    - properties for an equilibrium state 
    - what happens when there is a pertubation? 
- Description of graphs produce: 
   -  After the pertubation of an immigration of 50 individuals into species M population, both species were impacted - Species M increased, species N decreased - but they stabilised and returned to equilibrium.
   -  After the pertubation of an immigration of 200 individuals into species M population, both species were impacted - Species M increased, species N decreased - but they stabilised and returned to equilibrium.
   - After the changing alpha values to 0.9 for both species from 0.5, the Species N population increased until day 6, then rapidly decreased as species M population continued to increase until it plateaued at its carrying capacity 500. Species N then decreased until its population hit 0. at day 15, the population of M saw increase of 200 as an immigration occured. The increase of M continued increasing until carrying capacity and population N experienced a sudden drop in population, then a slow decline until population of 0. 

IC_Assignments4 - SIR disease modelling 
- The SIR model is a foundational mathematical framework used to simulate how infectious diseases spread through a population. It divides the population into three compartments:
    S (Susceptible): Individuals who are vulnerable to infection but not yet infected.
    I (Infectious): Individuals who are currently infected and can transmit the disease.
    R (Recovered): Individuals who have recovered and are assumed to be immune.
    The rates involved in the equation are beta which reflects the transmission rate. 

IC_inClassExample4 - SIR/SIZC modelling 
   - In this assignment we analysed the SIR model, in this case it was a SIZC model used in a journal article. The code was written in R, so we had to translate it using copilot or chatgpt. 
   - This was fairly smooth, although I saw some errors when I didn't have the scipy installed. After troubleshooting and asking chatgpt for the correct syntax the code worked and I eventually had to install pandas. Installing pandas was my last error.
   - The box and flow diagram included susceptible, infected, zoospores, carcesses of the salamander population and beta p, beta c and beta z as well as decay rate of carcasses, decay rate of the fungi zoospores, avg survival time (a), mew, and standard deviation variables. 