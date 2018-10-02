---
title: Lier des contrôles aux données dans Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- dislaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 85bfcb03ea2f383d8f1517d17c866c2320891aaa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504642"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Lier des contrôles aux données dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [lier des contrôles aux données dans Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).  
  
  
Vous pouvez afficher des données pour les utilisateurs de votre application en liant des données à des contrôles. Vous pouvez créer ces contrôles liés aux données en faisant glisser des éléments à partir de la **des Sources de données** fenêtre sur une aire de conception ou les contrôles sur une aire dans Visual Studio.  
  
 Cette rubrique décrit les sources de données que vous pouvez utiliser pour créer des contrôles liés aux données. Elle décrit également certaines des tâches générales qui entrent en jeu dans la liaison de données. Pour obtenir des détails plus spécifiques sur la création de contrôles liés aux données, consultez [lier les formulaires Windows contrôle aux données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) et [WPF de lier des contrôles à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
## <a name="data-sources"></a>Sources de données  
 Dans le contexte de liaison de données, une source de données représente les données en mémoire qui peut être lié à votre interface utilisateur. En pratique, une source de données peut être une classe d’Entity Framework, un jeu de données, un point de terminaison de service qui est encapsulé dans un objet de proxy .NET, une classe LINQ to SQL, ou n’importe quel objet .NET ou collection. Certaines sources de données permettent de créer des contrôles liés aux données en faisant glisser des éléments à partir de la **des Sources de données** fenêtre, contrairement à d’autres sources de données. Le tableau suivant affiche les sources de données qui sont prises en charge.  
  
|Source de données|Prise en charge du glisser-déplacer dans **le Concepteur de formulaires Windows**|Prise en charge du glisser-déplacer dans **le Concepteur WPF**|Prise en charge du glisser-déplacer dans **le Concepteur Silverlight**|  
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|  
|Groupe de données|Oui|Oui|Non|  
|Entity Data Model|Oui<sup>1</sup>|Oui|Oui|  
|Classes LINQ to SQL|Non<sup>2</sup>|Non<sup>2</sup>|Non<sup>2</sup>|  
|Services (y compris [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], WCF services et les services web)|Oui|Oui|Oui|  
|Object|Oui|Oui|Oui|  
|SharePoint|Oui|Oui|Oui|  
  
 1. Générer le modèle à l’aide de la **Entity Data Model** Assistant, puis faire glisser ces objets vers le concepteur.  
  
 2. Classes LINQ to SQL n’apparaissent pas dans le **des Sources de données** fenêtre. Toutefois, vous pouvez ajouter une nouvelle source de données Objet basée sur les classes LINQ to SQL, puis faire glisser ces objets vers le concepteur pour créer des contrôles liés aux données. Pour plus d’informations, consultez [procédure pas à pas : création de Classes LINQ to SQL (Concepteur O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).  
  
## <a name="data-sources-window"></a>Fenêtre Sources de données  
 Sources de données sont disponibles pour votre projet en tant qu’éléments dans le **des Sources de données** fenêtre. Cette fenêtre est visible, ou n’est accessible à partir de la **vue** menu, quand une aire de conception de formulaire est la fenêtre active dans votre projet. Vous pouvez faire glisser des éléments depuis cette fenêtre pour créer des contrôles liés aux données sous-jacentes, et vous pouvez également configurer les sources de données en effectuant un clic droit.  
  
 ![Fenêtre Sources de données](../data-tools/media/raddata-data-sources-window.png "fenêtre de Sources de données raddata")  
  
 Pour chaque type de données qui s’affiche dans le **des Sources de données** fenêtre, un contrôle par défaut est créé lorsque vous faites glisser l’élément vers le concepteur. Avant de faire glisser un élément à partir de la **des Sources de données** fenêtre, vous pouvez modifier le contrôle qui sera créé. Pour plus d’informations, consultez [définir le contrôle à créer lors du déplacement de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## <a name="tasks-involved-in-binding-controls-to-data"></a>Tâches impliquées dans la liaison de contrôles aux données  
 Le tableau suivant répertorie certaines des tâches plus courantes que vous effectuer pour lier des contrôles aux données.  
  
|Tâche|Complément d'information|  
|----------|----------------------|  
|Ouvrez le **des Sources de données** fenêtre.|Ouvrez une aire de conception dans l’éditeur et choisissez **vue** > **des Sources de données**.|  
|Ajouter une source de données à votre projet.|[Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)|  
|Définir le contrôle qui est créé lorsque vous faites glisser un élément à partir de la **des Sources de données** fenêtre vers le concepteur.|[Définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|  
|Modifier la liste des contrôles qui sont associés à des éléments dans le **des Sources de données** fenêtre.|[Ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md)|  
|Créer des contrôles liés aux données.|[Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)|  
|Lier à un objet ou de la collection.|[Lier des objets dans Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|  
|Filtrer les données qui s’affiche dans l’interface utilisateur.|[Guide pratique pour filtrer et trier des données dans une application Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|  
|Personnaliser des légendes pour les contrôles.|[Personnaliser la façon dont Visual Studio crée des légendes pour les contrôles liés aux données](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)   
 [Liaison de données Windows Forms](http://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa)

