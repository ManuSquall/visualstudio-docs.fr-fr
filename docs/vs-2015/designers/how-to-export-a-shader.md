---
title: 'Comment : exporter un nuanceur | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e8c3a6ea90b43caeb1140cbb9ab7c699bdb09c3e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49213289"
---
# <a name="how-to-export-a-shader"></a>Procédure : exporter un nuanceur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ce document indique comment utiliser le concepteur de nuanceur pour exporter un nuanceur DGSL (Directed Graph Shader Language) afin de pouvoir l’utiliser dans votre application.  
  
 Ce document illustre cette activité :  
  
-   Exportation d’un nuanceur  
  
## <a name="exporting-a-shader"></a>Exportation d’un nuanceur  
 Après avoir créé un nuanceur à l’aide du concepteur de nuanceur et pour pouvoir l’utiliser dans votre application, vous devez l’exporter dans un format pris en charge par votre API de graphismes. Vous pouvez exporter un nuanceur de différentes façons en fonction de vos besoins.  
  
#### <a name="to-export-a-shader"></a>Pour exporter un nuanceur  
  
1.  Dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ouvrez un fichier **Graphe de nuanceur visuel (.dgsl)**.  
  
     Si vous ne disposez pas d’un fichier **Graphe de nuanceur visuel (.dgsl)**, créez-en un en suivant la description de l’article [Comment : créer un nuanceur de couleur de base](../designers/how-to-create-a-basic-color-shader.md).  
  
2.  Dans la barre d’outils **Concepteur de nuanceur**, choisissez **Avancé**, **Exporter**, **Exporter en tant que**. La boîte de dialogue **Exporter le nuanceur** s’affiche.  
  
3.  Dans la liste déroulante **Type de fichier**, choisissez le format d’exportation souhaité.  
  
     Voici les formats que vous pouvez choisir :  
  
     **Nuanceur de pixels HLSL (\*.hlsl)**  
     Exporte le nuanceur comme code source HLSL (High Level Shader Language). Cette option permet de modifier le nuanceur ultérieurement, même après son déploiement dans une application. Elle peut faciliter le débogage et la mise à jour corrective du code basé sur les problèmes des utilisateurs finaux, mais elle permet également à un utilisateur de modifier plus facilement votre nuanceur de façon non souhaitée, par exemple, pour obtenir un avantage déloyal sur ses concurrents dans un jeu. Cette option peut également augmenter la durée de chargement du nuanceur.  
  
     **Nuanceur de pixels compilé (\*.cso)**  
     Exporte le nuanceur en tant que bytecode HLSL. Cette option permet de modifier le nuanceur ultérieurement, même après son déploiement dans une application. Elle peut faciliter le débogage et la mise à jour corrective du code basé sur les problèmes des utilisateurs finaux, mais comme le nuanceur est précompilé, elle n’entraîne pas de surcharge d’exécution supplémentaire lorsque le nuanceur est chargé par l’application. Les utilisateurs suffisamment compétents peuvent toujours modifier le nuanceur de manière indésirable, mais la compilation du nuanceur rend cette opération beaucoup plus difficile.  
  
     **En-tête C++ (\*.h)**  
     Exporte le nuanceur en tant qu’en-tête de style C qui définit un tableau d’octets contenant le bytecode HLSL. Cette option peut allonger la durée du débogage et de la mise à jour corrective du code basé sur les problèmes des utilisateurs finaux, car l’application doit être recompilée pour tester le correctif. Toutefois, comme cette option rend difficile, mais pas impossible, la modification du nuanceur après son déploiement dans une application, elle est celle qui présente le niveau de difficulté le plus élevé pour un utilisateur souhaitant modifier le nuanceur de manière indésirable.  
  
4.  Dans la zone de liste modifiable **Nom de fichier**, spécifiez un nom pour le nuanceur exporté, puis choisissez le bouton **Enregistrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer un nuanceur de couleur de base](../designers/how-to-create-a-basic-color-shader.md)   
 [Concepteur Shader](../designers/shader-designer.md)



