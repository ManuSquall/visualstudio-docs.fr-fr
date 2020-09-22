---
title: 'Comment : implémenter des marqueurs d’erreur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2af9e0765fb5bc73a35bebfc2f50f5d2a41122d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839638"
---
# <a name="how-to-implement-error-markers"></a>Guide pratique pour implémenter des marqueurs d’erreur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les marqueurs d’erreur (ou traits de soulignement ondulé rouge) sont les plus difficiles à implémenter dans l’éditeur de texte. Toutefois, les avantages qu’ils accordent aux utilisateurs de votre VSPackage peuvent être beaucoup plus importants que le coût de leur fourniture. Les marqueurs d’erreur marquent le texte que votre analyseur de langage estime incorrect avec une ligne rouge ondulée ou ondulée. Cet indicateur permet aux programmeurs d’afficher visuellement du code incorrect.  
  
 Utilisez des marqueurs de texte pour implémenter les soulignements ondulés rouges. En règle générale, les services de langage ajoutent des soulignements ondulés rouges à la mémoire tampon de texte en tant que passe en arrière-plan, soit au moment de l’inactivité, soit dans un thread d’arrière-plan.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>Pour implémenter la fonctionnalité de soulignement ondulé rouge  
  
1. Sélectionnez le texte sous lequel vous souhaitez placer la ligne ondulée rouge.  
  
2. Créez un marqueur de type `MARKER_CODESENSE_ERROR` . Pour plus d’informations, consultez [Comment : ajouter des marqueurs de texte standard](../extensibility/how-to-add-standard-text-markers.md).  
  
3. Après cela, transmettez un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> pointeur d’interface.  
  
   Ce processus vous permet également de créer du texte info-bulle ou un menu contextuel spécial sur un marqueur donné. Pour plus d’informations, consultez [Comment : ajouter des marqueurs de texte standard](../extensibility/how-to-add-standard-text-markers.md).  
  
   Les objets suivants sont requis pour que les marqueurs d’erreur puissent être affichés.  
  
- Analyseur.  
  
- Fournisseur de tâches (autrement dit, une implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> ) qui gère un enregistrement des modifications apportées aux informations de ligne afin d’identifier les lignes à réanalyser.  
  
- Filtre de vue de texte qui capture les événements de modification du signe insertion à partir de la vue à l’aide de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A> méthode).  
  
  L’analyseur, le fournisseur de tâche et le filtre fournissent l’infrastructure nécessaire pour rendre possible les marqueurs d’erreur. Les étapes suivantes décrivent le processus d’affichage des marqueurs d’erreur.  
  
1. Dans une vue filtrée, le filtre obtient un pointeur vers le fournisseur de tâches associé aux données de cette vue.  
  
    > [!NOTE]
    > Vous pouvez utiliser le même filtre de commande pour les conseils de méthode, la saisie semi-automatique des instructions, les marqueurs d’erreur, etc.  
  
2. Lorsque le filtre reçoit un événement indiquant que vous avez déplacé vers une autre ligne, une tâche est créée pour rechercher les erreurs éventuelles.  
  
3. Le gestionnaire de tâches vérifie si la ligne a été modifiée. Dans ce cas, la ligne est analysée pour les erreurs.  
  
4. Si des erreurs sont détectées, le fournisseur de tâche crée une instance d’élément de tâche. Cette instance crée le marqueur de texte que l’environnement utilise comme marqueur d’erreur dans l’affichage de texte.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Comment : ajouter des marqueurs de texte standard](../extensibility/how-to-add-standard-text-markers.md)   
 [Comment : créer des marqueurs de texte personnalisés](../extensibility/how-to-create-custom-text-markers.md)   
 [Guide pratique pour utiliser des marqueurs de texte](../extensibility/how-to-use-text-markers.md)
