---
title: 'Procédure : Utiliser la recherche dans le concepteur de workflow'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 52adbded9f570689cd5749cc620ca8f74222e308
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854670"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Procédure : Utiliser la recherche dans le concepteur de workflow

Pour faciliter la création de flux de travail plus volumineuses et complexes, vous pouvez rechercher dans le Concepteur de flux de travail pour rechercher des éléments par mot clé. Notez que le concepteur ne prend pas en charge l'activité Replace.

## <a name="quick-find"></a>Recherche rapide

Recherche rapide identifie les éléments suivants dans le concepteur :

-   Propriétés des objets <xref:System.Activities.Activity>, des objets <xref:System.Activities.Statements.FlowNode>, des objets <xref:System.Activities.Statements.State>, des transitions, et d'autres éléments de contrôle de flux personnalisés.

-   Variables

-   Arguments

-   Expressions

### <a name="use-quick-find"></a>Utiliser la recherche rapide

1. Avec le Concepteur de flux de travail ouvert, appuyez sur **Ctrl + F**, ou sélectionnez **modifier** > **rechercher et remplacer** > **recherche rapide**.

2. Entrez le terme de recherche dans les **rechercher** zone de texte et cliquez sur **suivant**.

3. Le terme de recherche se trouve dans le flux de travail en cours. L’illustration suivante montre un nom complet d’activité qui se trouve dans le concepteur :

   ![Résultats de la recherche dans le concepteur de flux de travail](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Rechercher dans les fichiers

Rechercher dans les fichiers localise les chaînes dans les fichiers de flux de travail, y compris les fichiers XAML.

### <a name="use-find-in-files"></a>Utiliser la commande Rechercher dans les fichiers

1.  Dans Visual Studio, appuyez sur **Ctrl**+**MAJ**+**F**, ou sélectionnez **modifier**  >   **Rechercher et remplacer** > **rechercher dans les fichiers**.

2.  Entrez l’élément recherché dans le **rechercher** zone de texte et cliquez sur **Rechercher tout**.

3.  Résultat de la recherche est indiqué dans le **résultat de la recherche** vue. Double-cliquez sur un élément de résultat navigue vers l’activité qui contient la correspondance dans le Concepteur de flux de travail.