---
title: Lier des contrôles à des données
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- displaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 31e2086126e9a17554c80b53858205e83fd504fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673037"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Lier des contrôles à des données dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez afficher des données pour les utilisateurs de votre application en liant des données à des contrôles. Vous pouvez créer ces contrôles liés aux données en faisant glisser des éléments depuis la fenêtre **sources de données** vers une aire de conception ou des contrôles sur une surface dans Visual Studio.

 Cette rubrique décrit les sources de données que vous pouvez utiliser pour créer des contrôles liés aux données. Elle décrit également certaines des tâches générales qui entrent en jeu dans la liaison de données. Pour plus d’informations sur la façon de créer des contrôles liés aux données, consultez [lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) et [lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="data-sources"></a>Sources de données
 Dans le contexte de la liaison de données, une source de données représente les données en mémoire qui peuvent être liées à votre interface utilisateur. En pratique, une source de données peut être une classe Entity Framework, un DataSet, un point de terminaison de service encapsulé dans un objet proxy .NET, une classe LINQ to SQL ou n’importe quel objet ou collection .NET. Certaines sources de données vous permettent de créer des contrôles liés aux données en faisant glisser des éléments de la fenêtre **Sources de données**, contrairement à d’autres sources de données. Le tableau suivant affiche les sources de données qui sont prises en charge.

|Source de données|Prise en charge du glisser-déplacer dans le **Concepteur Windows Forms**|Prise en charge du glisser-déplacer dans le **Concepteur WPF**|Prise en charge du glisser-déplacer dans le **Concepteur Silverlight**|
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|
|Dataset|Oui|Oui|Non|
|Entity Data Model|Oui<sup>1</sup>|Oui|Oui|
|Classes LINQ to SQL|Non <sup>2</sup>|Non <sup>2</sup>|Non <sup>2</sup>|
|Services (notamment [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], les services WCF et les services web)|Oui|Oui|Oui|
|Object|Oui|Oui|Oui|
|SharePoint|Oui|Oui|Oui|

 1. Générez le modèle à l’aide de l’Assistant **Entity Data Model** , puis faites glisser ces objets vers le concepteur.

 2. Les classes LINQ to SQL ne s’affichent pas dans la fenêtre **Sources de données**. Toutefois, vous pouvez ajouter une nouvelle source de données Objet basée sur les classes LINQ to SQL, puis faire glisser ces objets vers le concepteur pour créer des contrôles liés aux données. Pour plus d’informations, consultez [procédure pas à pas : création de Classes LINQ to SQL (Concepteur O-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).

## <a name="data-sources-window"></a>Fenêtre Sources de données
 Les sources de données peuvent être utilisées par votre projet sous la forme d’éléments dans la fenêtre **Sources de données**. Cette fenêtre est visible, ou est accessible à partir du menu **affichage** , lorsqu’une aire de conception de formulaire est la fenêtre active de votre projet. Vous pouvez faire glisser des éléments à partir de cette fenêtre pour créer des contrôles liés aux données sous-jacentes, et vous pouvez également configurer les sources de données en cliquant avec le bouton droit.

 ![Fenêtre sources de données](../data-tools/media/raddata-data-sources-window.png "fenêtre sources de données raddata")

 Pour chaque type de données qui apparaît dans la fenêtre **Sources de données**, un contrôle par défaut est créé quand vous faites glisser l’élément vers le concepteur. Avant de faire glisser un élément de la fenêtre **sources de données** , vous pouvez modifier le contrôle qui sera créé. Pour plus d’informations, consultez [définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="tasks-involved-in-binding-controls-to-data"></a>Tâches impliquées dans la liaison de contrôles à des données
 Le tableau suivant répertorie certaines des tâches les plus courantes que vous effectuez pour lier des contrôles à des données.

|Tâche|Informations complémentaires|
|----------|----------------------|
|Ouvrez la fenêtre **Sources de données**.|Ouvrez une aire de conception dans l’éditeur, puis choisissez **Afficher**les  >  **sources de données**.|
|Ajoutez une source de données à votre projet.|[Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)|
|Définissez le contrôle créé lorsque vous faites glisser un élément de la fenêtre **Sources de données** vers le concepteur.|[Définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|Modifiez la liste des contrôles associés aux éléments dans la fenêtre **Sources de données**.|[Ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Créer des contrôles liés aux données.|[Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)|
|Lier à un objet ou une collection.|[Lier des objets dans Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|
|Filtrer les données qui s’affichent dans l’interface utilisateur.|[Guide pratique pour filtrer et trier des données dans une application Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Personnaliser les légendes pour les contrôles.|[Personnaliser la façon dont Visual Studio crée des légendes pour les contrôles liés aux données](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Voir aussi
 Liaison [de données de Visual Studio Data Tools pour .net](../data-tools/visual-studio-data-tools-for-dotnet.md) [Windows Forms](https://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa)
