<center>
<h1><b>Predicting Land Cover Change</b></h1>
<h2>By using remote sensing data - within the act of compromising AI & Blockchain.</h2>
<h5>Project code name: <b>PathAwayer</b></h5>

</center>
<p><font face="cambria" color="gray"><i>** This project is carried out within my doctoral studies, which is researching artificial intelligence blockchain interoperability.</i></font></p>

<font face="cambria" color="gray"><i>** This notebook has been inspired by the [Chris Brown & Nick Clinton EarthEngine + Tensorflow presentation](https://www.youtube.com/watch?v=w-1xfF0IaeU). It shows the step by step how to integrate Google Earth Engine and TensorFlow 2.0 in the same pipeline (EE->Tensorflow->EE).
  
The landcover codes used are inspired by the works of [Cesar Aybar](https://csaybar.github.io/).
The collective learning codes adapted from [Fecth.ai Colearn Github Repository](https://github.com/fetchai/colearn/) 
 </i></font>

---

<h2>Introduction</h2>
<p>As a result of recent advances in remote sensing (RS) technology, huge amounts of RS images have been acquired and stored in massive archives, from which the mining of useful information is an important and challenging issue.

When data is produced at unprecedented speed, in high volume, and at distributed locations, aggregating it to a centralized location, such as cloud, for centralized machine learning (ML) is a formidable if not impractical hurdle.

In a centralized machine learning approach, the training data is aggregated to a centralized location, where machine models are developed, trained, and tested. 

In centralized computing such as the cloud, machine learning can be carried out centrally, which can substantially increase the amount of data available for training and thereby improve machine learning results. But this poses disadvantages such as data duplication and increased data traffic as well as challenges for data privacy and security.

One major challenge to the centralized learning approach is the increasingly distributed nature of data, driven by the proliferation of data sources around us. 

Data sovereignty, security, and privacy can all create barriers to transferring and aggregating the vast amount of data required to train ML models. In addition, the costs of a central infrastructure to host and process the aggregated data can be prohibitive.

Decentralized AI solutions would overcome current shortcomings that accommodate inherently distributed data structures and data privacy and security regulations.

Distributed machine learning based on standardized AI engines with a blockchain can be securely onboard members, dynamically elect the leader among members, and merge model parameters.
</p>

<h2>Future Aspects of AI & Blockchain Symbiosis</h2>
<p>We would need a framework to enable decentralized training of machine learning models without sharing the data.

This framework should able to make it possible for a set of nodes—each node possessing some training data locally—to train a common machine learning model collaboratively without sharing the training data.

This can be achieved by individual nodes sharing parameters (weights) derived from training the model on the local data.
This allows local measures at the nodes to maintain the confidentiality and privacy of the raw data.

In contrast to many existing federated learning models, any central parameter server should be omitted.

The framework can inherit developments to further preserve privacy such as differential privacy algorithms, functional encryption, encrypted transfer learning, or homomorphic encryption approaches.

The framework itself does not rely on a fixed central aggregator but instead implements a dynamic selection of changing aggregators for every merge cycle by means of smart contracts.

The framework should interact with other peers using blockchain for sharing parameters and for controlling the training process.

A new node enrolls via a blockchain smart contract, obtains the model, and performs local model training until defined conditions for synchronization are met. 

Next, model parameters are exchanged via an application programming interface (API) and merged to create an updated model with updated parameter settings before starting a new training round.
</p>

<h2>Current solutions on the way of AI & Blockchain Symbiosis</h2>
A solution, called collective learning, suitable for the above context is being developed by the startup company, [Fetch ai](https://fetch.ai/).

<h5>What is Collective Learning</h5>

Collective Learning or colearn is a library that enables privacy-preserving decentralized machine learning tasks on the [FET network](https://fetch.ai/).

**Blockchain**-mediated collective learning system enables multiple stakeholders to build a shared machine learning model without needing to rely on a central authority, and without revealing sensitive information about their dataset to the other stakeholders.

The collective learning protocol allows learners to collaborate on training a model without requiring trust between the participants. Learners vote on updates to the model, and only updates which pass the quality threshold are accepted. This makes the system robust to attempts to interfere with the model by providing bad updates.

For more information [Fetch.ai Colearn Web Site](https://docs.fetch.ai/colearn/)

<h5>How Training Works</h5>
Training occurs in rounds; during each round the learners attempt to improve the performance of the global shared model. To do so each round an update of the global model (for example a new set of weights in a neural network) is proposed. The learners then evaluate the update and decide if the new model is better than the current global model.

The detailed steps of a round updating a global model M are as follows:


*   One of the learners is selected and proposes a new updated model M’
*   The rest of the learners validate M’
*   If M’ has better performance than M against their private data set then the learner votes to approve
*   If not the learner votes to reject
*   The total votes are tallied
*   If more than some threshold (typically 50%) of learners approve then M’ becomes the new global model. If not, M continues to be the global model
*   A new round begins.

<center>
<img src="https://fetch.ai/wp-content/uploads/2020/06/Collective-Learning-Graphic-New.png" with="400" height="400">
</center> 

You can review the open source code on Collective Learning [Github repository](https://github.com/fetchai/colearn)

<h2>Problem Area</h2>
<p>The natural land cover of the earth has been subjected to great changes over many years depending on human activities and different usage methods.

Large cities in developing countries are subject to a dynamic urbanization process because of population growth and migration. Since the acceleration of the urbanization process, settlement components that are built continuously cause significant changes in land cover and use.

These changes have a negative effect on the natural cover and **ecosystem**. Therefore, regular follow-up of changes due to urbanization and detecting the current situation is important.

One of the most important image processing techniques in **remote sensing** science is *classification*. Utilizing the **Deep Neural Network** (DNN) binary-classification in prediction with remote sensing images, many use cases can be applied, such as land cover and usage purpose, water resources management, and change analysis.

In this project, by using remote sensing satellite images, it's tried to estimate the vegetation cover and residential areas at a simple level with DNN binary classification for the Marmaris region in 2019.
</p>
<h2>Using Platforms</h2>
<p>As a senior solutions architect who always tries to find the most optimized way, I guess the below architecture would be more sensible for this research project.</p>

*   [Earth Engine](https://earthengine.google.com/) — geospatial analysis platform
*   [Earth Engine Data Catalog](https://developers.google.com/earth-engine/datasets/) — comprehensive archive of geospatial data (including NLCD)
*   [TensorFlow](https://www.tensorflow.org/) — machine learning platform with FCNN capabilities
*   [AI Platform](https://cloud.google.com/ai-platform/) — TensorFlow model training
*   [Colab](http://colab.research.google.com/) — Jupyter notebook server for workflow development
<center>
<img src="https://miro.medium.com/max/3200/0*xVXtPYUw8h2bvd7M">
</center> 

<h2>Data from Earth Engine</h2>

Within the scope of the project, the [Landsat 8 Surface Reflectance Tier 1](https://developers.google.com/earth-engine/datasets/catalog/LANDSAT_LC08_C01_T1_SR) data set, *freely available to use* - by Google Earth Engine (GEE) was used.
LANDSAT satellites, a joint program of USGS and NASA, provide images of the entire earth's surface at a resolution of 30 meters every two weeks, including multispectral and thermal data.

This dataset is atmospheric corrected surface reflection from Landsat 8 OLI / TIRS sensors. These images contain 5 visible and near infrared (VNIR) bands and 2 short-wave infrared (SWIR) bands processed into orthorectified surface reflection and two thermal infrared (TIR) ​​bands processed to orthorectified luminance temperature.

The data obtained are stored separately for each band detected by the sensor. In order to create a multicolored image, band merging of the downloaded image has been done. For the purpose of this study, a multicolored image was created by combining Red-Green-Blue and Near Infrared bands (Band 2-Band 3- Band 4-Band 5 for Landsat 8).

<h3>Prediction Area</h3>

In the project, an area of approximately 10 km2 (3.5km x 3km) that will cover the **Marmaris** / Akyaka, Turkey environment is determined as the prediction area and the model is arranged to be made prediction over this area.


<center>
<img src="https://media-exp1.licdn.com/dms/image/C4D22AQHEl6i4NLL-Ng/feedshare-shrink_800/0/1619435849862?e=1623283200&v=beta&t=30ypGSa85v0plKJ8Z94kD26ykIHqYUwSSGw9XBmpSPU">
</center> 

<h3>Classification of Satellite Images</h3>

Data sets consist of 2 classes via Google Earth Engine; [1] It is simply classified into Vegetation (green dots) and [2] Settlement Area (red dots), with 800 (400: [1] - 400: [2]) training and 200 (100: [1]) - 100: [2]) tagged via GEE as the test data set. The mentioned labeling table has been saved as an asset in GEE.

<h2>Methods</h2>

In this project, [TensorFlow Keras Sequential model](https://www.tensorflow.org/guide/keras/sequential_model) is used as the DNN model.
While the model is being trained, **Keras callback** editor calls have been added, which allow monitoring the training process in order to accelerate convergence, avoid overfitting and reach the most optimum model.

**validation_loss** is set to halt the training process if it loses value at 10 epochs. Finally, in the model, the **ModelCheckpoint** function has been adjusted to get the value where the **validation_loss** value reaches the best value by saving it to the given variable.

The model compilation is **Stochastic Gradient Descent (SGD)** and **binary_crossentropy** loss function is used for its optimization.
