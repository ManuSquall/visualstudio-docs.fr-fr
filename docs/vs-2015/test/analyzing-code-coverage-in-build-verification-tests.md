---
title: Analyse de la couverture du code dans les tests de vérification de build | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 59c07d15-511e-4fd0-b398-bde9d5ed00d9
caps.latest.revision: 10
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e7525fe8e01922880199275576a8b12ec29bc029
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834931"
---
# <a name="analyzing-code-coverage-in-build-verification-tests"></a>Analyse de la couverture du code dans les tests de vérification de build
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’analyse de la couverture du code dans Microsoft Visual Studio vous montre le volume de code traité par les tests automatisés. Pour plus d’informations, consultez [Utilisation de la couverture du code pour déterminer la quantité de code testé](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
 Lorsque vous archivez votre code, vos tests s’exécutent sur le serveur de builds, avec l’ensemble des tests des autres membres de l’équipe. (Si vous ne l’avez pas déjà fait, consultez [Exécuter des tests dans votre processus de génération](http://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38).) L’analyse de la couverture du code dans le service de build est très utile, car elle permet d’obtenir l’image la plus récente et la plus complète de la couverture du code dans le projet entier. Elle inclut également des tests système automatisés et d'autres tests codés qui ne sont généralement pas exécutés sur les ordinateurs de développement.  
  
1. Dans Team Explorer, ouvrez **Builds**, puis ajoutez ou modifiez une définition de build.  
  
2. Dans la page **Processus**, développez **Tests automatisés**, **Source de test**, **Paramètres d’exécution**. Affectez à **Type des paramètres d’exécution** la valeur **Couverture du code activée**.  
  
    Si vous avez plusieurs définitions de source de test, répétez cette étape pour chaque définition.  
  
   - <em>Mais aucun champ n’est nommé **Type de fichier des paramètres d’exécution</em>*.*  
  
      Sous **Tests automatisés**, sélectionnez **Assembly de test**, puis choisissez le bouton de sélection **[...]** situé à la fin de la ligne. Dans la boîte de dialogue **Ajouter/Modifier une série de tests**, sous **Test Runner**, choisissez **Visual Studio Test Runner**.  
  
   ![Définition de build pour la couverture du code](../test/media/codecoverage-plaincc.png "CodeCoverage-plainCC")  
  
   Après l’exécution de la build, les résultats de la couverture du code s’affichent dans le résumé de la build.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de la couverture du code pour déterminer la quantité de code testé](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
