## LOADING AND UNLOADING CHARECTERISTICS OF MATERIALS

This repository contains the code work that i did during my Bachelors as part of my project, wherein I attempted to predict the loading, unloading charecteristics of materials using their properties, which reduces the time to design the sample, experiment, and test the sample to find the stress-strain graph (loading, unloading charecteristics). (I cannot release the the data, and complete outputs of my work as it is confidential).

 The stress-strain graph of a material is a fundamental tool for understanding how the material respond to mechanical loading and is essential for the design and analysis of engineering structures. Existing method to plot or find the stree-strain graph (or relation) involves preparing a sample of the material and testing in UTM (Universal Testing Machine) or any other sophisticated mmachine. This is resource and time intensive, in order to test one sample, the sample have to be carefully cut or made in a specific shape that can be fit in the machine and then tested. One wrong mistake (in design or composition of the material) causes wastage of time and work. On succesfull testing, we will get a graph, which shows the variation of stress w.r.t strain in loading and unloading phase (which can be linear unlaonding or exponential unloading). The machine shows the stress and strain at different timesteps and also the stress-strain plot of these datapoints.

 Loading and Unloading can be of several kinds, in general, there are two kings 'Linear' and 'Exponential'.

 Linear Loading/Unloading: During linear loading or unloading the material's behaviour follows the equation - Y = a(x) + b, where a, b are coefficients and can be found by observing the stress-strain plot obtained from the above experiment. (fitting the data on a curve fitting software gives us the coefficients)
 Exponential: During exponential loading or unloading the material's behaviour follows the equation - Y = a*(e^(-bx)) + c, where a, b and c are coefficients and can be found from the stress-strain plot obtained from the above experiment.

Existing approaches requires carefull preparation and testing of the sample to find the loading and unloading charecteristic (graph or plot), which, as dicussed above, is resource and time intensive. With Machine Learning and Neural Network gaining importance in every field, I incorporated ANN (Articficial Neural Network) in our work to find the charecteristic equation(a, b, c values) of the stress-strain plot of the material using its deformation properties ('Loading Plasticity Value','Unloading Plasticity','Coefficient Plasticity Depth','Coefficient Adhesion'). Since this is supervised learning, we extracted some of the data from existing SQL database using simple queries and able to get 4,274 samples data.

Data is carefully cleaned for any missing values or outliers in presence of shcolars, and ANN model's are built for the prediction of the charecteristics of the plot. My idea is that, we use one ANN for finding the loading charecteristics (to find the equation in loading phase), and 2 more ANN's to find the Linear unloading and Exponential unloading charecterisitics. We first trained a ANN (with architecture 64-32-3), which seems to be best from all of our testings, that can predict the loading coefficients (a, b and c). And 2 more ANN's with (64-32-2, 64-32-3) for Linear Unloading and Exponential Unloading were trained. We used 'MSE', 'RMSE', 'MAE' as our metric and 'AIC', 'BIC' scores to compare the perfromance w.r.t complexity of different architectures.

At the end, after vigorous and careful hyper parameter tuning, we were able to achieve good scores, with the predicted values being close to the actual values.


![f928b0a7-5068-44c2-884c-820ce2735e57](https://github.com/pbt12/BTP-1-Prediction-of-Loading-and-Unloading-Charecteristics-/assets/74967927/04784127-447d-4651-af5b-4792a1e5a2d0)

Above image is the scatter plot of actual and predicted a_UL, b_UL, and c_UL (for exponential unloading scenario). We can see that the actual values are close to the predicted values. Apart from this, we trained another ANN to identify whether the unloading phase follows linear or exponential fashion, once we found out what type it follows, then we use the particular type ANN and get the plot or charecteristic.

This is first phase of my project, wherein we try to predict the materials stress strain behaviour given its deformation properties. My second part of the project involves solving the inverse problem which is, I want to know the defromation behaviour of the material that follows a certain linear or exponential loading and unloading charecteristic. This is something new, till now I have deformation behaviour and I found its stress-strain equation, but now I have to solve the inverse problem. The codes for this inverse problem can be found here.



The file 'Loading_Unloading_fit.ipynb' contains the code that I implemented for the above work.





