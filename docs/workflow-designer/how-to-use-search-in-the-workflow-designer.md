---
title: 'Procédure : utiliser la fonction de recherche dans le Concepteur de flux de travail'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 12bda4af085b8ab41d3e11841f24cd5dfd389738
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650296"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Procédure : utiliser la fonction de recherche dans le Concepteur de flux de travail

Pour faciliter la création de flux de travail plus volumineux et plus complexes, vous pouvez rechercher des éléments par mot clé dans le Concepteur de flux de travail. Notez que le concepteur ne prend pas en charge l'activité Replace.

## <a name="quick-find"></a>Recherche rapide

La recherche rapide recherche les éléments suivants dans le concepteur :

- Propriétés des objets <xref:System.Activities.Activity>, des objets <xref:System.Activities.Statements.FlowNode>, des objets <xref:System.Activities.Statements.State>, des transitions, et d'autres éléments de contrôle de flux personnalisés.

- Variables

- Arguments

- Expressions

### <a name="use-quick-find"></a>Utiliser la recherche rapide

1. Avec le concepteur de flux de travail ouvert, appuyez sur **Ctrl + F**, ou sélectionnez **modifier**  > **Rechercher et remplacer**  > **recherche rapide**.

2. Entrez le terme de recherche dans la zone de texte **Rechercher** , puis cliquez sur **suivant**.

3. Le terme de recherche se trouve dans le flux de travail actuel. L’illustration suivante montre le nom complet d’une activité qui se trouve dans le concepteur :

   ![Résultats de la recherche dans le concepteur de flux de travail](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Rechercher dans les fichiers

Rechercher dans les fichiers localise les chaînes dans les fichiers de flux de travail, y compris les fichiers XAML.

### <a name="use-find-in-files"></a>Utiliser Rechercher dans les fichiers

1. Dans Visual Studio, appuyez sur **Ctrl** +**MAJ** +**F**, ou sélectionnez **modifier**  > **Rechercher et remplacer**  > **Rechercher dans les fichiers**.

2. Entrez l’élément de recherche dans la zone de texte **Rechercher** , puis cliquez sur **Rechercher tout**.

3. Le résultat de la recherche est affiché dans la vue résultat de la **recherche** . Double-cliquez sur un élément de résultat pour accéder à l’activité qui contient la correspondance dans le concepteur de Workflow.