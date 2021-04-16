# La Ségmentation des Images de la Microscopie Électronique
## Implémentation du framework ```U-net``` du deep learning, en utilisant ```Keras```

## Introduction:

* Contexte du projet:

L’IA est aujourd’hui omniprésente dans la littérature scientifique de l’imagerie médicale, d’autant plus depuis le développement de nouveaux algorithmes appelés réseaux de neurones convolutifs

En effet, à ce jour, l’IA est très utile dans le domaine de l’imagerie, sur deux volets : la classification des images et la segmentation des organes. Les algorithmes pour classifier les images peuvent permettre d’aider au diagnostic en classant une image dans une catégorie particulière de pathologie. Les algorithmes pour segmenter les images sont couramment utilisés sur tous les types d’imagerie et en routine au CHRU. C’est ainsi que l’IA permet un gain de temps aux praticiens à la fois pour le diagnostic ou lors d’interventions. Elle présente aussi l’avantage de contourner certains biais liés à l’interprétation de l’opérateur.

L'architecture a été inspirée par ```U-Net```: Convolutional Networks for Biomedical Image Segmentation.

## Description des données

Les données du projet contiennent ```30 images``` d'une résolution de ```512*512```, ce qui est loin d'être suffisant pour alimenter un réseau de neurones d'apprentissage en profondeur. J'utilise un module appelé ```ImageDataGenerator``` dans ```keras.preprocessing.image``` pour augmenter les données (fichier dataPrepare.ipynb). 
Les targets sont des masques d'images, et non pas des catégories discrètes. Chaque donnée est une paire d'images (l'image normale et le masque avec les contours).

## Dépendances 
* Ce didacticiel dépend des bibliothèques suivantes:
```
    Tensorflow
    Keras >= 1.0
```

## Modèle
![images/u-net-architecture.png](images/u-net-architecture.png)

## Entainement du modèle
* Le modèle est formé pour 5 époques.
* Après 5 époques, la précision calculée est d'environ 0,97.
* La fonction de perte pour l'entraînement n'est en fait qu'une crossentropie binaire.

## Présentation de l'architecture utilisée
Utilisez le modèle entraîné pour effectuer une segmentation sur des images de test, le résultat:
<br>
![Animation](images/Animation-Input-Labels.gif)
<br>

## Conclusion (avantages et inconvénients, concurrents, recommandations…)

* À propos de Keras:

Keras est une bibliothèque de réseaux de neurones minimaliste et hautement modulaire, écrite en Python et capable de fonctionner sur TensorFlow ou Theano. Il a été développé dans le but de permettre une expérimentation rapide. Être capable de passer de l'idée au résultat avec le moins de retard possible est essentiel pour faire de bonnes recherches.

Utilisez Keras si vous avez besoin d'une bibliothèque d'apprentissage en profondeur qui:

    Permet un prototypage simple et rapide (grâce à une modularité totale, un minimalisme et une extensibilité).
    Prend en charge à la fois les réseaux convolutifs et les réseaux récurrents, ainsi que les combinaisons des deux.
    Prend en charge les schémas de connectivité arbitraires (y compris la formation multi-entrées et multi-sorties).
    Fonctionne de manière transparente sur le CPU et le GPU. 

[Lire la documentation de Keras](https://keras.io/)


