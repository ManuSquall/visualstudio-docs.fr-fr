---
title: 'Procédure : exporter un nuanceur'
description: Découvrez comment utiliser le concepteur Shader pour exporter un nuanceur de langage de nuanceur de graphique orienté pour pouvoir l’utiliser dans votre application.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7f4abcdf5648031be9b76ba3f25e0a8f33d4efba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930965"
---
# <a name="how-to-export-a-shader"></a>Guide pratique pour exporter un nuanceur

Cet article indique comment utiliser le **Concepteur de nuanceur** pour exporter un nuanceur DGSL (Directed Graph Shader Language) afin de pouvoir l’utiliser dans une application.

## <a name="export-a-shader"></a>Exporter un nuanceur

Après avoir créé un nuanceur à l’aide du concepteur de nuanceur et pour pouvoir l’utiliser dans votre application, vous devez l’exporter dans un format pris en charge par votre API de graphismes. Vous pouvez exporter un nuanceur de différentes façons en fonction de vos besoins.

1. Dans Visual Studio, ouvrez un fichier **Visual Shader Graph (.dgsl)**.

     Si vous ne disposez pas d’un fichier **Graphe de nuanceur visuel (.dgsl)**, créez-en un en suivant la description de l’article [Guide pratique pour créer un nuanceur de couleur de base](../designers/how-to-create-a-basic-color-shader.md).

2. Dans la barre d’outils **Concepteur de nuanceur**, choisissez **Avancé** > **Exporter** > **Exporter en tant que**. La boîte de dialogue **Exporter le nuanceur** apparaît.

3. Dans la liste déroulante **Type de fichier**, choisissez le format d’exportation souhaité.

     Voici les formats que vous pouvez choisir :

     **Nuanceur de pixels HLSL (\*.hlsl)** Exporte le nuanceur comme code source HLSL (High Level Shader Language). Cette option permet de modifier le nuanceur ultérieurement, même après son déploiement dans une application. Elle peut faciliter le débogage et la mise à jour corrective du code basé sur les problèmes des utilisateurs finaux, mais elle permet également à un utilisateur de modifier plus facilement votre nuanceur de façon non souhaitée, par exemple, pour obtenir un avantage déloyal sur ses concurrents dans un jeu. Cette option peut également augmenter la durée de chargement du nuanceur.

     **Nuanceur de pixels compilé (\*.cso)** Exporte le nuanceur comme bytecode HLSL. Cette option permet de modifier le nuanceur ultérieurement, même après son déploiement dans une application. Elle peut faciliter le débogage et la mise à jour corrective du code basé sur les problèmes des utilisateurs finaux, mais comme le nuanceur est précompilé, elle n’entraîne pas de surcharge d’exécution supplémentaire lorsque le nuanceur est chargé par l’application. Les utilisateurs suffisamment compétents peuvent toujours modifier le nuanceur de manière indésirable, mais la compilation du nuanceur rend cette opération beaucoup plus difficile.

     **En-tête C++ (\*.h)** Exporte le nuanceur en tant qu’en-tête de style C qui définit un tableau d’octets contenant le bytecode HLSL. Cette option peut allonger la durée du débogage et de la mise à jour corrective du code basé sur les problèmes des utilisateurs finaux, car l’application doit être recompilée pour tester le correctif. Toutefois, comme cette option rend difficile, mais pas impossible, la modification du nuanceur après son déploiement dans une application, elle est celle qui présente le niveau de difficulté le plus élevé pour un utilisateur souhaitant modifier le nuanceur de manière indésirable.

4. Dans la zone de liste modifiable **Nom de fichier**, spécifiez un nom pour le nuanceur exporté, puis choisissez le bouton **Enregistrer**.

## <a name="see-also"></a>Voir aussi

- [Comment : créer un nuanceur de couleur de base](../designers/how-to-create-a-basic-color-shader.md)
- [Concepteur Shader](../designers/shader-designer.md)
