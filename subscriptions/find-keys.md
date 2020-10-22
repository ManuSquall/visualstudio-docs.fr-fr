---
title: Recherche et réclamation de clés de produit dans les abonnements Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: cabuschl
ms.assetid: da8df006-4896-4ff9-b487-698d78deabc3
ms.date: 07/30/2020
ms.topic: conceptual
description: Découvrir comment rechercher, réclamer et exporter des clés de produit dans les abonnements Visual Studio
ms.openlocfilehash: a246f66e429b78647f217468c7c19b703b419062
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "91004965"
---
# <a name="finding-and-claiming-product-keys-in-visual-studio-subscriptions"></a>Recherche et réclamation de clés de produit dans les abonnements Visual Studio
Cet article explique comment localiser, réclamer et exporter des clés de produit à partir de https://my.visualstudio.com/productkeys.  Pour plus d’informations sur l’activation d’un produit avec une clé, sur les versions commerciales et de licence en volume des clés ainsi que sur les limites quotidiennes de réclamations de clés de produit, consultez la [vue d’ensemble des clés de produit](product-keys.md).

## <a name="locating-and-claiming-product-keys"></a>Recherche et demande de clés de produit
Vous devez être connecté à votre abonnement Visual Studio pour afficher vos clés de produit. Pour rechercher des clés de produit, sélectionnez le lien bleu **Obtenir une clé** d’un produit spécifique dans la page [Téléchargements](https://my.visualstudio.com/downloads), comme illustré ci-dessous.  Toutes les clés disponibles sont également regroupées dans la page [Clés de produit](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs). Quand plusieurs clés d’un même produit sont disponibles, des remarques sont affichées dans la colonne Remarques du téléchargement pour vous aider à identifier la clé appropriée.
> [!div class="mx-imgBorder"]
> ![Obtenir une clé à partir de la page Téléchargements](_img/product-keys/download-get-key.png "Sélectionnez obtenir une clé sur la page d’informations de n’importe quel téléchargement pour obtenir une clé pour ce produit.")

Certains produits regroupent plusieurs éditions du produit en un seul téléchargement. Dans ces cas de figure, la clé de produit entrée détermine l’édition du produit installée.
Certaines clés sont fournies automatiquement, comme les clés « statiques » qui peuvent être utilisées un nombre de fois illimité, car elles ne nécessitent aucune activation. D’autres clés doivent être demandées à l’aide du lien **Obtenir une clé** correspondant au produit.

Différents types de clés sont disponibles en fonction du produit.

### <a name="product-key-types"></a>Types de clés de produit

|    Type de clé           |    Description                                                                                                                                                                                                           |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Non applicable                    |    L’installation de ce produit ne nécessite pas de clé.                                                       |
|    Retail                     |    Les clés de produit commercialisé permettent plusieurs activations et sont utilisées pour les versions commercialisées du produit. Généralement, dix activations sont autorisées par clé, même si un plus grand nombre est souvent permis sur une même machine.                                                       |
|    Activation multiple        |    Une clé d’activation multiple (MAK) vous permet d’activer plusieurs installations d’un produit avec la même clé. Les clés MAK sont généralement utilisées avec les versions de licence en volume d’un produit. En règle générale, une seule clé MAK est fournie par abonnement.    |
|    Clé d’activation statique    |    Les clés d’activation statiques sont fournies pour les produits qui n’ont pas besoin d’être activés. Elles peuvent être utilisées pour un nombre illimité d’installations.                                                                                                                  |
|    Clé personnalisée                 |    Les clés personnalisées fournissent des actions ou informations spéciales pour activer ou installer le produit.                                                                                                                                                                |
|    VA 1.0                     |    Ce sont des clés d’activation multiple, similaires aux clés MAK.                                                                                                                                                                                                 |
|    Clé OEM                    |    Ce sont des clés de fabricant OEM qui permettent plusieurs activations.                                                                                                                                                                       |
|    Clé de produit commercialisé DreamSpark    |    Ces clés de produit commercialisé concernent les programmes DreamSpark et permettent une seule activation. Les clés de produit commercialisé DreamSpark sont émises par lots et sont essentiellement destinées aux étudiants.                                                                                     |
|    Clé lab DreamSpark         |    Ces clés lab DreamSpark sont utilisées dans les environnements lab des programmes DreamSpark et permettent plusieurs activations. Elles sont destinées aux scénarios de laboratoires informatiques universitaires.                                                                                       |
|    Clé MAK DreamSpark         |    Ce sont des clés MAK destinées aux clients des programmes DreamSpark.                                                                                                                                                                                                  |
|

Vous pouvez demander une clé à partir de la page Téléchargements du produit, ou rechercher la clé dont vous avez besoin dans la page [Clés de produit](https://my.visualstudio.com/productkeys).

### <a name="claiming-product-keys"></a>Demande de clés de produit
Seuls les abonnés ayant des abonnements actifs peuvent télécharger des produits et demander des clés de produit.  Si vous avez un abonnement actif, vous pouvez exporter vos clés demandées à partir de la page [Clés de produit](https://my.visualstudio.com/productkeys).

Pour demander une clé de produit :
1. Connectez-vous à votre abonnement Visual Studio.  Vous devez être connecté pour pouvoir télécharger des produits ou demander des clés de produit.
2. Sélectionnez l’onglet [clés de produit](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) .
3. Les clés de produit sont répertoriées par nom de produit, par ordre alphabétique.  Vous pouvez faire défiler la liste jusqu’au nom de produit recherché, ou rechercher le produit à l’aide de la barre de recherche en haut de la page.
> [!div class="mx-imgBorder"]
> ![Rechercher une clé de produit](_img/product-keys/search-keys.png "Faites défiler jusqu’au produit souhaité ou utilisez la zone de recherche pour localiser rapidement un produit.")
   
Dans cet exemple, nous avons utilisé la barre de recherche afin de localiser une clé de produit pour Visual Studio Enterprise 2019.
Comme vous pouvez le constater, plusieurs versions sont listées.  Chacune des clés a déjà été réclamée pour les versions 16.0 et 16.1 de Visual Studio Enterprise 2019.  Des clés supplémentaires de types distincts sont toujours disponibles pour les deux versions. Notez que vous pouvez enregistrer une brève remarque sur les clés demandées dans la colonne **Remarques**.  Vous pouvez utiliser cette colonne conjointement avec la date de la colonne **Demandé** pour suivre les clés que vous avez demandées.  Par exemple, ajoutez une remarque quand vous activez une installation du produit à l’aide de la clé.

### <a name="exporting-your-claimed-keys"></a>Exportation de vos clés demandées
Vous pouvez exporter une liste de toutes les clés que vous avez demandées, et d’un grand nombre de clés statiques et d’autres clés qui sont automatiquement marquées comme « demandées » pour vous.

> [!IMPORTANT]
> Si votre abonnement expire, vous ne pouvez plus demander de nouvelles clés ou exporter les clés demandées.

Pour exporter vos clés, il vous suffit de sélectionner le lien **exporter toutes les clés** à l’extrême droite de la page clés de produit.  Un fichier .xml intitulé KeysExport.xml est créé. Vous pouvez ensuite ouvrir ou enregistrer le fichier.  Vous devez ouvrir le fichier avec une application prenant en charge les fichiers .xml.  Par exemple, vous pouvez ouvrir le fichier en tant que classeur en lecture seule dans Excel.

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
Une fois que vous êtes prêt à télécharger le logiciel et à utiliser les clés, accédez à https://my.visualstudio.com/downloads.  Pour plus d’informations sur le téléchargement de logiciels, consultez la [vue d’ensemble du téléchargement](download-software.md).