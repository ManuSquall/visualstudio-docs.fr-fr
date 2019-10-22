---
title: 'Comment : utiliser la recherche dans le Concepteur de flux de travail | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 84f74b4718a7f976b386197a79692256ab49caa4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659120"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Procédure : utiliser la fonction de recherche dans le Concepteur de flux de travail
Pour faciliter la création de workflows de plus grande taille et plus complexes, Rechercher peut être utilisé dans le concepteur de workflow pour rechercher des éléments par mot clé. Notez que le concepteur ne prend pas en charge l'activité Replace. La recherche va trouver les éléments suivants dans le concepteur :

## <a name="quick-find"></a>Recherche rapide
 La recherche rapide recherchera les éléments suivants dans le concepteur :

- Propriétés des objets <xref:System.Activities.Activity>, des objets <xref:System.Activities.Statements.FlowNode>, des objets <xref:System.Activities.Statements.State>, des transitions, et d'autres éléments de contrôle de flux personnalisés.

- Variables

- Arguments

- Expressions

#### <a name="using-quick-find"></a>Utilisation de la fonction Recherche rapide

1. Avec le concepteur de flux de travail ouvert, appuyez sur **Ctrl + F**, ou sélectionnez **modifier**, **Rechercher et remplacer**, **recherche rapide**.

2. Entrez le terme de recherche dans la zone de texte **Rechercher** , puis cliquez sur **suivant**.

3. Le terme de recherche se trouve dans le workflow actif. La capture d'écran suivante affiche le nom complet de l'activité qui se trouve dans le concepteur.

     ![Résultats de la recherche dans le Concepteur de flux de travail](../workflow-designer/media/designersearch.png "DesignerSearch")

## <a name="find-in-files"></a>Rechercher dans les fichiers
 Utilisez Rechercher dans les fichiers pour localiser des chaînes dans les fichiers de workflow, notamment les fichiers XAML.

#### <a name="using-find-in-files"></a>Utilisation de Rechercher dans les fichiers

1. Dans Visual Studio, appuyez sur **Ctrl + Maj + F**, ou sélectionnez **modifier**, **Rechercher et remplacer**, **Rechercher dans les fichiers** .

2. Entrez l’élément de recherche dans la zone de texte **Rechercher** , puis cliquez sur **Rechercher tout** .

3. Le résultat de la recherche sera affiché dans la vue résultat de la**recherche** [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Double-cliquez sur un élément de résultat pour accéder à l'activité qui contient la correspondance dans le concepteur de workflow.