---
title: 'Procédure : utiliser la fonction de recherche dans le Concepteur de flux de travail'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 4b5dfdd4b4d05969406f93801bcf87880949e41a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Procédure : utiliser la fonction de recherche dans le Concepteur de flux de travail

Pour faciliter la création de workflows de plus grande taille et plus complexes, Rechercher peut être utilisé dans le concepteur de workflow pour rechercher des éléments par mot clé. Notez que le concepteur ne prend pas en charge l'activité Replace. La recherche va trouver les éléments suivants dans le concepteur :

## <a name="quick-find"></a>Recherche rapide

Recherche rapide identifie les éléments suivants dans le concepteur :

-   Propriétés des objets <xref:System.Activities.Activity>, des objets <xref:System.Activities.Statements.FlowNode>, des objets <xref:System.Activities.Statements.State>, des transitions, et d'autres éléments de contrôle de flux personnalisés.

-   Variables

-   Arguments

-   Expressions

### <a name="using-quick-find"></a>Utilisation de la fonction Recherche rapide

1.  Avec le Concepteur de flux de travail ouvert, appuyez sur **Ctrl + F**, ou sélectionnez **modifier**, **rechercher et remplacer**, **recherche rapide**.

2.  Entrez le terme de recherche dans les **rechercher** zone de texte et cliquez sur **suivant**.

3.  Le terme de recherche se trouve dans le workflow actif. La capture d'écran suivante affiche le nom complet de l'activité qui se trouve dans le concepteur.

     ![Résultat de la recherche dans le Concepteur de flux de travail](../workflow-designer/media/designersearch.png "DesignerSearch")

## <a name="find-in-files"></a>Rechercher dans les fichiers

Utilisez Rechercher dans les fichiers pour localiser des chaînes dans les fichiers de workflow, notamment les fichiers XAML.

### <a name="using-find-in-files"></a>Utilisation de Rechercher dans les fichiers

1.  Dans Visual Studio, appuyez sur **Ctrl + Maj + F**, ou sélectionnez **modifier**, **rechercher et remplacer**, **rechercher dans les fichiers**

2.  Entrez le texte recherché dans le **rechercher** zone de texte et cliquez sur **Rechercher tout**

3.  Résultat de la recherche s’affichera dans Visual Studio**résultat de la recherche** vue. Double-cliquez sur un élément de résultat pour accéder à l'activité qui contient la correspondance dans le concepteur de workflow.