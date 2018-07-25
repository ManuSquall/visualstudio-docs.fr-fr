---
title: Guide pratique pour exporter un nuanceur
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1eb69a4662521c08fc8d2df34bbbfa41a5d1d7ea
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924077"
---
# <a name="how-to-export-a-shader"></a>Guide pratique pour exporter un nuanceur
Ce document indique comment utiliser le concepteur de nuanceur pour exporter un nuanceur DGSL (Directed Graph Shader Language) afin de pouvoir l’utiliser dans votre application.

 Ce document illustre cette activité :

-   Exportation d’un nuanceur

## <a name="exporting-a-shader"></a>Exportation d’un nuanceur
 Après avoir créé un nuanceur à l’aide du concepteur de nuanceur et pour pouvoir l’utiliser dans votre application, vous devez l’exporter dans un format pris en charge par votre API de graphismes. Vous pouvez exporter un nuanceur de différentes façons en fonction de vos besoins.

### <a name="to-export-a-shader"></a>Pour exporter un nuanceur

1.  Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ouvrez un fichier **Graphe de nuanceur visuel (.dgsl)**.

     Si vous ne disposez pas d’un fichier **Graphe de nuanceur visuel (.dgsl)**, créez-en un en suivant la description de l’article [Guide pratique pour créer un nuanceur de couleur de base](../designers/how-to-create-a-basic-color-shader.md).

2.  Dans la barre d’outils **Concepteur de nuanceur**, choisissez **Avancé** > **Exporter** > **Exporter en tant que**. La boîte de dialogue **Exporter le nuanceur** apparaît.

3.  Dans la liste déroulante **Type de fichier**, choisissez le format d’exportation souhaité.

     Voici les formats que vous pouvez choisir :

     **Nuanceur de pixels HLSL (\*.hlsl)** Exporte le nuanceur comme code source HLSL (High Level Shader Language). Cette option permet de modifier le nuanceur ultérieurement, même après son déploiement dans une application. Elle peut faciliter le débogage et la mise à jour corrective du code basé sur les problèmes des utilisateurs finaux, mais elle permet également à un utilisateur de modifier plus facilement votre nuanceur de façon non souhaitée, par exemple, pour obtenir un avantage déloyal sur ses concurrents dans un jeu. Cette option peut également augmenter la durée de chargement du nuanceur.

     **Nuanceur de pixels compilé (\*.cso)** Exporte le nuanceur comme bytecode HLSL. Cette option permet de modifier le nuanceur ultérieurement, même après son déploiement dans une application. Elle peut faciliter le débogage et la mise à jour corrective du code basé sur les problèmes des utilisateurs finaux, mais comme le nuanceur est précompilé, elle n’entraîne pas de surcharge d’exécution supplémentaire lorsque le nuanceur est chargé par l’application. Les utilisateurs suffisamment compétents peuvent toujours modifier le nuanceur de manière indésirable, mais la compilation du nuanceur rend cette opération beaucoup plus difficile.

     **En-tête C++ (\*.h)** Exporte le nuanceur en tant qu’en-tête de style C qui définit un tableau d’octets contenant le bytecode HLSL. Cette option peut allonger la durée du débogage et de la mise à jour corrective du code basé sur les problèmes des utilisateurs finaux, car l’application doit être recompilée pour tester le correctif. Toutefois, comme cette option rend difficile, mais pas impossible, la modification du nuanceur après son déploiement dans une application, elle est celle qui présente le niveau de difficulté le plus élevé pour un utilisateur souhaitant modifier le nuanceur de manière indésirable.

4.  Dans la zone de liste modifiable **Nom de fichier**, spécifiez un nom pour le nuanceur exporté, puis choisissez le bouton **Enregistrer**.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer un nuanceur de couleur de base](../designers/how-to-create-a-basic-color-shader.md)
- [Concepteur Shader](../designers/shader-designer.md)