## Effects of Extended Features on BERT Performance: Depression Detection

<b>Official implementation of the [SIU 2025](https://siu2025.isikun.edu.tr/index_en.php) paper.</b>

Emirhan Balcı*, Esra Saraç

## Abstract
In this study, the effects of categorical and numerical additional features obtained from Twitter posts on depression detection were investigated. Depression detection performances of the BERT large language model and SVM classifier were compared on the dataset balanced with the oversampling method. The effects of two different feature addition methods, Unimodal and Concat, were evaluated on the BERT model. The results show that oversampling improves the performance of the BERT classifier, but feature addition methods do not provide a significant improvement in the model performance. The findings of the experiments reveal the success of the BERT model in the field of classification and that it does not require additional features for the detection of depression. It is believed that this study will guide research in the field of depression detection and help researchers identify more effective areas of study.

[Code](https://github.com/BashMocha/Extended-Features-on-BERT-Performance/tree/master/notebooks) | [Paper]() | [Data](https://github.com/BashMocha/Extended-Features-on-BERT-Performance/tree/master/data)

## Updates

25/06/2025: We release the utilized dataset and the source code.

13/05/2025: The study is accepted by SIU 2025! 🎉

09/02/2025: The paper is submitted to the symposium.

## Addition of Extended Features into BERT
To enhance the feature representations obtained from the BERT model, two techniques from the open-source Python library [Multimodal-Toolkit](https://github.com/georgian-io/Multimodal-Toolkit/tree/master), developed for integrating numerical and categorical features into Transformer-based models, were employed. In the method referred to as Unimodal, categorical and numerical attributes are appended to the corresponding posts in textual form, and the resulting text is tokenized prior to being input into the BERT model for training. In the Concat approach, encoded categorical values—converted into numerical representations—along with the numerical features, are concatenated with the word embedding vector of the respective post and passed to the final classification layers.

To detect depression, five distinct feature representations were defined to characterize the structural and contextual properties of each post. These representations include two numerical features—such as the length of the post and the number of profane words it contains—and three categorical features indicating the presence of positive emojis, negative emojis, or URL links within the post.

In the Unimodal approach, the extended features were incorporated into the corresponding posts prior to tokenization, whereas in the Concat approach, they were concatenated with the word embedding vectors of the respective posts. Within the Unimodal method, categorical features were encoded using binary values to provide numerical representations, while numerical features were normalized using a quantile-based transformation to approximate a Gaussian distribution. This normalization process ensured compatibility between the numerical features and the word embeddings derived from the BERT model, and contributed to a more stable learning process by reducing the influence of outliers.
<br><br>

![1](https://github.com/user-attachments/assets/48345570-cd9a-4020-9c44-dc910f89a346)
<div align="center">
  <p>Visualization of the applied Unimodal method.</p>
</div><br>


![1(1)](https://github.com/user-attachments/assets/61a5fe91-ea44-4289-b7cb-6e783fc66245)
<div align="center">
  <p>Visualization of the applied Concat method.</p>
</div>
<br>

The extended features were appended to the word embedding vectors of the corresponding posts produced by the encoder layers of the BERT model, thereby increasing the embedding dimension from 768 to 773. The resulting word embedding vectors were subsequently fed into the BERT classifier.

![2](https://github.com/user-attachments/assets/d75881c6-fd7f-4e59-b0ac-8178d3391f84)

## Results

<div align="center">
<table>
  <thead>
    <tr>
      <th>Feature Type</th>
      <th>Training Method</th>
      <th>F1</th>
      <th>F1-micro</th>
      <th>F1-macro</th>
      <th>F1-weighted</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="2">Original</td>
      <td>holdout</td>
      <td>0.95</td>
      <td>0.95</td>
      <td>0.95</td>
      <td>0.95</td>
    </tr>
    <tr>
      <td>5-fold</td>
      <td>1.00</td>
      <td>1.00</td>
      <td>1.00</td>
      <td>1.00</td>
    </tr>
    <tr>
      <td rowspan="2">Unimodal</td>
      <td>holdout</td>
      <td>0.95</td>
      <td>0.95</td>
      <td>0.95</td>
      <td>0.95</td>
    </tr>
    <tr>
      <td>5-fold</td>
      <td>0.99</td>
      <td>0.99</td>
      <td>0.99</td>
      <td>0.99</td>
    </tr>
    <tr>
      <td rowspan="2">Concat</td>
      <td>holdout</td>
      <td>0.94</td>
      <td>0.94</td>
      <td>0.94</td>
      <td>0.94</td>
    </tr>
    <tr>
      <td>5-fold</td>
      <td>1.00</td>
      <td>1.00</td>
      <td>1.00</td>
      <td>1.00</td>
    </tr>
  </tbody>
</table>
</div>
<br>

When training was conducted on the BERT+BERT model using the Concat and Unimodal methods, it was observed that both approaches yielded similar results. The holdout and 5-fold cross-validation results obtained using the Concat method were recorded as 0.94 and 1.00, respectively, while those obtained using the Unimodal method were 0.95 and 0.99. The outcomes from both the Unimodal and Concat methods are quite close to the results achieved by training the BERT+BERT model solely with oversampling. Specifically, the 5-fold cross-validation result obtained with the Unimodal method and the holdout result obtained with the Concat method were each 0.01 lower than the corresponding results from training the model solely with oversampling. These findings suggest that the contribution of the additional features integrated into the BERT model may be limited in improving classification performance for depression detection.

## Citation

If you find the dataset or code useful, please cite:

```bibtex
@inproceedings{balci_extended_2025,
	title = {Effects of Extended Features on BERT Performance: Depression Detection},
	booktitle = {2025 33rd IEEE Conference on Signal Processing and Communications Applications (SIU2025},
	author = {Balcı, Emirhan and Saraç, Esra},
	year = {2025},
}
```

## License

MIT License

<hr>

Feel free to [contact](mailto:emirbalci360@gmail.com) for any questions.
