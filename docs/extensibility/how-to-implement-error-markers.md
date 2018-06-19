---
title: 'Comment : implémenter des marqueurs d’erreur | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f1360f88dba797f96af766f65c9ee41abd6fc808
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127850"
---
# <a name="how-to-implement-error-markers"></a>Comment : implémenter des marqueurs d’erreur
Marqueurs d’erreur (ou des soulignements ondulés rouges) sont les personnalisations de l’éditeur de texte pour implémenter la plus difficile. Toutefois, les avantages que leur donnent aux utilisateurs de votre VSPackage peuvent compensent le coût pour les fournir. Marqueurs d’erreur légèrement marquer le texte que votre analyseur de langage juge incorrecte d’un trait rouge sinueux ou par des soulignements ondulés. Cet indicateur permet aux programmeurs en affichant visuellement de code incorrect.  
  
 Utiliser des marqueurs de texte pour implémenter des soulignements ondulés rouges. En règle générale, les services de langage ajouter des soulignements ondulés rouges à la mémoire tampon de texte en tant qu’une passe en arrière-plan, à la durée d’inactivité ou dans un thread d’arrière-plan.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>Pour implémenter la fonctionnalité de soulignement ondulé rouge  
  
1.  Sélectionnez le texte dans lequel vous souhaitez placer la ligne ondulée rouge.  
  
2.  Créer un marqueur de type `MARKER_CODESENSE_ERROR`. Pour plus d’informations, consultez [Comment : ajouter des marqueurs de texte Standard](../extensibility/how-to-add-standard-text-markers.md).  
  
3.  Après cela, passez un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> pointeur d’interface.  
  
 Ce processus permet également de vous permet de créer le texte info-bulle ou un menu contextuel spéciaux sur un marqueur donné. Pour plus d’informations, consultez [Comment : ajouter des marqueurs de texte Standard](../extensibility/how-to-add-standard-text-markers.md).  
  
 Les objets suivants sont requis avant l’affichage de marqueurs d’erreur.  
  
-   Un analyseur.  
  
-   Un fournisseur de tâche (autrement dit, une implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>) qui conserve un enregistrement des modifications dans les informations de ligne afin d’identifier les lignes pour être réanalysé.  
  
-   Événements de modification d’un filtre d’affichage de texte qui capture le point d’insertion à partir de la vue à l’aide de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>) méthode.  
  
 L’analyseur, le fournisseur de tâche et le filtre fournissent l’infrastructure nécessaire pour rendre les marqueurs d’erreur possible. Les étapes suivantes décrivent le processus pour l’affichage des marqueurs d’erreur.  
  
1.  Dans une vue est filtrée, le filtre Obtient un pointeur vers le fournisseur de tâche associé à données ses.  
  
    > [!NOTE]
    >  Vous pouvez utiliser le même filtre de commande pour la méthode conseils, saisie semi-automatique des instructions, des marqueurs d’erreur et ainsi de suite.  
  
2.  Lorsque le filtre reçoit un événement indiquant que vous avez déplacé vers une autre ligne, une tâche est créée pour rechercher des erreurs.  
  
3.  Le Gestionnaire de tâches vérifie si la ligne n’est pas intègre. Dans ce cas, il analyse la ligne pour les erreurs.  
  
4.  Si des erreurs sont détectées, le fournisseur de tâche crée une instance d’élément de tâche. Cette instance crée le marqueur de texte qui utilise de l’environnement comme un marqueur d’erreur dans l’affichage de texte.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de marqueurs de texte avec l’API hérité](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Comment : ajouter des marqueurs de texte Standard](../extensibility/how-to-add-standard-text-markers.md)   
 [Comment : créer des marqueurs de texte personnalisé](../extensibility/how-to-create-custom-text-markers.md)   
 [Comment : utiliser des marqueurs de texte](../extensibility/how-to-use-text-markers.md)