---
title: Lier des contrôles Windows Forms à des données
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
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 866b2b824735ed96615880350343d17adfeecefc
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59653994"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Lier des contrôles Windows Forms à des données dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez afficher des données aux utilisateurs de votre application en liant des données à des Windows Forms. Pour créer ces contrôles liés aux données, vous pouvez faire glisser des éléments à partir de la **des Sources de données** fenêtre jusqu’au Concepteur Windows Forms dans Visual Studio. Cette rubrique décrit certaines des tâches, outils et classes impliquées dans la création d’applications de Windows Forms lié aux données plus courants.

 ![Opération de glissement de Source de données](../data-tools/media/raddata-data-source-drag-operation.png "opération de glissement raddata Source de données")

 Pour obtenir des informations générales sur la création de contrôles liés aux données dans Visual Studio, consultez [lier des contrôles aux données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Pour plus d’informations sur la liaison de données dans les Windows Forms, consultez [liaison de données Windows Forms](http://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa).

## <a name="in-this-section"></a>Dans cette section

-   [Lier des contrôles Windows Forms à des données](../data-tools/bind-windows-forms-controls-to-data.md)

-   [Valider des modifications in-process sur des contrôles liés aux données avant d’enregistrer des données](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)

-   [Créer des tables de recherche dans des applications Windows Forms](../data-tools/create-lookup-tables-in-windows-forms-applications.md)

-   [Créer un Windows Form pour rechercher des données](../data-tools/create-a-windows-form-to-search-data.md)

-   [Créer un contrôle utilisateur Windows Forms prenant en charge la liaison de données simples](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)

-   [Procédure pas à pas : création d’un contrôle utilisateur Windows Forms prenant en charge la liaison de données complexes](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)

-   [Créer un contrôle utilisateur Windows Forms prenant en charge la liaison de données complexes](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)

-   [Passer des données entre des formulaires](../data-tools/pass-data-between-forms.md)

## <a name="bindingsource-component"></a>BindingSource (composant)
 Le composant <xref:System.Windows.Forms.BindingSource> remplit deux fonctions. Tout d’abord, il fournit une couche d’abstraction lors de la liaison des contrôles sur votre formulaire à des données. Contrôles du formulaire sont liés à la <xref:System.Windows.Forms.BindingSource> composant (au lieu d’être lié directement à une source de données).

 Deuxièmement, il peut gérer une collection d’objets. Ajout d’un type à la <xref:System.Windows.Forms.BindingSource> crée une liste de ce type.

 Pour plus d’informations sur le <xref:System.Windows.Forms.BindingSource> composant, consultez :

-   [BindingSource, composant](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)

-   [Vue d'ensemble du composant BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)

-   [Architecture du composant BindingSource](http://msdn.microsoft.com/library/7bc69c90-8a11-48b1-9336-3adab5b41591)

## <a name="bindingnavigator-control"></a>BindingNavigator (contrôle)
 Ce composant fournit une interface utilisateur pour parcourir les données affichées par une application Windows. Pour plus d'informations, consultez [BindingNavigator, contrôle](http://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).

## <a name="datagridview-control"></a>DataGridView (contrôle)
 Pour afficher et modifier des données tabulaires à partir de différents types de sources de données, utilisez la <xref:System.Windows.Forms.DataGridView> contrôle. Vous pouvez lier des données à un <xref:System.Windows.Forms.DataGridView> à l’aide de la <xref:System.Windows.Forms.DataGridView.DataSource%2A> propriété. Pour plus d’informations, consultez [vue d’ensemble du contrôle DataGridView](http://msdn.microsoft.com/library/0a45c661-89dc-4390-9cc6-c47eee501488).

## <a name="see-also"></a>Voir aussi
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
