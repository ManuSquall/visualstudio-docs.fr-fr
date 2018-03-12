---
title: "Comment : utiliser la recherche dans le Concepteur de flux de travail | Documents Microsoft"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 0ab8fe2ca639dd4660dfbabc8c5497f4ab0b3487
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Procédure : utiliser la fonction de recherche dans le Concepteur de flux de travail
Pour faciliter la création de workflows de plus grande taille et plus complexes, Rechercher peut être utilisé dans le concepteur de workflow pour rechercher des éléments par mot clé. Notez que le concepteur ne prend pas en charge l'activité Replace. La recherche va trouver les éléments suivants dans le concepteur :  
  
## <a name="quick-find"></a>Recherche rapide  
 La recherche rapide recherchera les éléments suivants dans le concepteur :  
  
-   Propriétés des objets <xref:System.Activities.Activity>, des objets <xref:System.Activities.Statements.FlowNode>, des objets <xref:System.Activities.Statements.State>, des transitions, et d'autres éléments de contrôle de flux personnalisés.  
  
-   Variables  
  
-   Arguments  
  
-   Expressions  
  
#### <a name="using-quick-find"></a>Utilisation de la fonction Recherche rapide  
  
1.  Avec le Concepteur de flux de travail ouvert, appuyez sur **Ctrl + F**, ou sélectionnez **modifier**, **rechercher et remplacer**, **recherche rapide**.  
  
2.  Entrez le terme de recherche dans les **rechercher** zone de texte et cliquez sur **suivant**.  
  
3.  Le terme de recherche se trouve dans le workflow actif. La capture d'écran suivante affiche le nom complet de l'activité qui se trouve dans le concepteur.  
  
     ![Résultat de la recherche dans le Concepteur de flux de travail](../workflow-designer/media/designersearch.png "DesignerSearch")  
  
## <a name="find-in-files"></a>Rechercher dans les fichiers  
 Utilisez Rechercher dans les fichiers pour localiser des chaînes dans les fichiers de workflow, notamment les fichiers XAML.  
  
#### <a name="using-find-in-files"></a>Utilisation de Rechercher dans les fichiers  
  
1.  Dans Visual Studio, appuyez sur **Ctrl + Maj + F**, ou sélectionnez **modifier**, **rechercher et remplacer**, **rechercher dans les fichiers**  
  
2.  Entrez le texte recherché dans le **rechercher** zone de texte et cliquez sur **Rechercher tout**  
  
3.  Résultat de la recherche s’affichera dans le [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] **résultat de la recherche** vue. Double-cliquez sur un élément de résultat pour accéder à l'activité qui contient la correspondance dans le concepteur de workflow.