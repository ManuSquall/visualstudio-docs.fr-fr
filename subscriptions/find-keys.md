---
title: Recherche et réclamation de clés de produit dans les abonnements Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: cabuschl
ms.assetid: da8df006-4896-4ff9-b487-698d78deabc3
ms.date: 02/18/2021
ms.topic: conceptual
description: Découvrir comment rechercher, réclamer et exporter des clés de produit dans les abonnements Visual Studio
ms.openlocfilehash: 5e055295e76ee91dbaf641256b8b7e93a530fcfb
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249269"
---
# <a name="finding-and-claiming-product-keys-in-visual-studio-subscriptions"></a>Recherche et réclamation de clés de produit dans les abonnements Visual Studio
Cet article explique comment localiser, réclamer et exporter des clés de produit à partir de https://my.visualstudio.com/productkeys.  Pour plus d’informations sur l’activation d’un produit avec une clé, les versions commerciales et de licence en volume des clés, ainsi que les limites de la revendication de clé de produit quotidienne, consultez la [vue d’ensemble des clés de produit](product-keys.md).

## <a name="locating-and-claiming-product-keys"></a>Recherche et demande de clés de produit
Vous devez être connecté à votre abonnement Visual Studio pour afficher vos clés de produit. Pour rechercher des clés de produit, sélectionnez le lien bleu **Obtenir une clé** d’un produit spécifique dans la page [Téléchargements](https://my.visualstudio.com/downloads), comme illustré ci-dessous.  Toutes les clés disponibles sont également regroupées dans la page [Clés de produit](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs). Quand plusieurs clés d’un même produit sont disponibles, des remarques sont affichées dans la colonne Remarques du téléchargement pour vous aider à identifier la clé appropriée.
> [!div class="mx-imgBorder"]
> ![Obtenir une clé à partir de la page Téléchargements](_img/product-keys/download-get-key.png "Sélectionnez obtenir une clé sur la page d’informations de n’importe quel téléchargement pour obtenir une clé pour ce produit.")

Certains produits regroupent plusieurs éditions du produit en un seul téléchargement. Dans ces cas de figure, la clé de produit entrée détermine l’édition du produit installée.
Certaines clés sont fournies automatiquement, comme les clés « statiques » qui peuvent être utilisées un nombre de fois illimité, car elles ne nécessitent aucune activation. D’autres clés doivent être demandées à l’aide du lien **Obtenir une clé** correspondant au produit.

Différents types de clés sont disponibles, en fonction du produit.

### <a name="product-key-types"></a>Types de clés de produit

|    Type de clé           |    Description                                                                                                                                                                                                           |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Non applicable                    |    L’installation de ce produit ne nécessite pas de clé.                                                       |
|    Commerce                     |    Les clés de produit commercialisé permettent plusieurs activations et sont utilisées pour les versions commercialisées du produit. Généralement, dix activations sont autorisées par clé, même si un plus grand nombre est souvent permis sur une même machine.                                                       |
|    Activation multiple        |    Une clé d’activation multiple (MAK) vous permet d’activer plusieurs installations d’un produit avec la même clé. Les MAK sont utilisées avec les versions de licence en volume des produits. En règle générale, une seule clé MAK est fournie par abonnement.    |
|    Clé d’activation statique    |    Les clés d’activation statiques sont fournies pour les produits qui n’ont pas besoin d’être activés. Elles peuvent être utilisées pour un nombre illimité d’installations.                                                                                                                  |
|    Clé personnalisée                 |    Les clés personnalisées fournissent des actions ou informations spéciales pour activer ou installer le produit.                                                                                                                                                                |
|    VA 1.0                     |    Plusieurs clés d’activation, similaires à une clé MAK.                                                                                                                                                                                                 |
|    Clé OEM                    |    Clés du fabricant de l’équipement d’origine qui autorisent plusieurs activations.                                                                                                                                                                       |
|    Clé de produit commercialisé DreamSpark    |    Les clés de vente au détail pour DreamSpark autorisent une activation. Les clés de produit commercialisé DreamSpark sont émises par lots et sont essentiellement destinées aux étudiants.                                                                                     |
|    Clé lab DreamSpark         |    Lab utilise des clés pour les programmes DreamSpark qui autorisent plusieurs activations. Elles sont destinées aux scénarios de laboratoires informatiques universitaires.                                                                                       |
|    Clé MAK DreamSpark         |    Clés MAK pour les clients du programme DreamSpark.                                                                                                                                                                                                  |
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
Comme vous pouvez le constater, plusieurs versions sont listées.  Chacune des clés a déjà été réclamée pour les versions 16.0 et 16.1 de Visual Studio Enterprise 2019.  Des clés supplémentaires de types distincts sont toujours disponibles pour les deux versions. Notez que vous pouvez enregistrer une brève remarque sur les clés demandées dans la colonne **Remarques**.  Vous pouvez l’utiliser avec la date de la colonne **revendiqué** pour suivre les clés que vous avez demandées.  Par exemple, ajoutez une remarque quand vous activez une installation du produit à l’aide de la clé.

### <a name="exporting-your-claimed-keys"></a>Exportation de vos clés demandées
Vous pouvez exporter une liste des clés que vous avez demandées.  Cela comprend une large sélection de clés statiques et autres qui sont automatiquement marquées comme « réclamées ».

> [!IMPORTANT]
> Si votre abonnement expire, vous ne pouvez plus demander de nouvelles clés ou exporter les clés demandées.

Pour exporter vos clés, sélectionnez le lien **exporter toutes les clés** à l’extrême droite de la page clés de produit.  Un fichier. xml intitulé KeysExport.xml est créé, et vous pouvez choisir d’ouvrir ou d’enregistrer le fichier.  Vous devez ouvrir le fichier avec une application prenant en charge les fichiers .xml.  Par exemple, vous pouvez ouvrir le fichier en tant que classeur en lecture seule dans Excel.

## <a name="resources"></a>Ressources
- [Prise en charge des abonnements Visual Studio](https://my.visualstudio.com/gethelp)

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
Une fois que vous êtes prêt à télécharger le logiciel et à utiliser les clés, accédez à https://my.visualstudio.com/downloads.  Pour plus d’informations sur le téléchargement de logiciels, consultez la [vue d’ensemble du téléchargement](download-software.md).