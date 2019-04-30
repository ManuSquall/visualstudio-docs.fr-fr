---
title: Créer des tables de recherche dans les applications Windows Forms | Microsoft Docs
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
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: adea3666c3f8b8d78c37b32a1a42f7f8b270369c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431171"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Créer des tables de recherche dans des applications Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le terme *table de recherche* décrit les contrôles qui sont liés aux tables de données connexes deux. Ces contrôles de recherche affichent les données à partir de la première table selon une valeur sélectionnée dans la seconde table.  
  
 Vous pouvez créer des tables de recherche en faisant glisser le nœud principal d’une table parent (à partir de la [fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)) sur un contrôle de votre formulaire qui est déjà lié à la colonne dans la table enfant connexe.  
  
 Par exemple, considérez une table de `Orders` dans une base de données de ventes. Chaque enregistrement dans le `Orders` table inclut un `CustomerID`, indiquant le client ayant passé la commande. Le `CustomerID` est une clé étrangère pointant vers un enregistrement de client dans le `Customers` table. Dans ce scénario, vous développez le `Orders` table dans le **des Sources de données** fenêtre et la valeur est le nœud principal **détails**. Définissez ensuite la `CustomerID` colonne à utiliser un <xref:System.Windows.Forms.ComboBox> (ou tout autre contrôle qui prend en charge la liaison de correspondance) et faites glisser le `Orders` nœud vers votre formulaire. Enfin, faites glisser le `Customers` nœud sur le contrôle qui est lié à la colonne associée, dans ce cas, le <xref:System.Windows.Forms.ComboBox> lié à la `CustomerID` colonne.  
  
## <a name="to-databind-a-lookup-control"></a>Pour lier un contrôle de recherche  
  
1. Ouvrez la fenêtre **Sources de données**.  
  
    > [!NOTE]
    > Les tables de recherche nécessitent que les deux tables ou objets connexes sont disponibles dans le **des Sources de données** fenêtre.
  
2. Développez les nœuds dans le **des Sources de données** fenêtre jusqu'à ce que vous pouvez voir la table parente et toutes ses colonnes et la table enfant connexe et toutes ses colonnes.  
  
    > [!NOTE]
    > Le nœud de la table enfant est le nœud qui apparaît sous la forme d’un nœud enfant développable dans la table parente.  
  
3. Modifier le type de déplacement de la table enfant à **détails** en sélectionnant **détails** à partir de la liste de contrôle sur le nœud de la table enfant. Pour plus d’informations, consultez [définir le contrôle à créer lors du déplacement de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
4. Recherchez le nœud qui lie les deux tables (le `CustomerID` nœud dans l’exemple précédent). Modifiez son type de déplacement à un <xref:System.Windows.Forms.ComboBox> en sélectionnant **ComboBox** à partir de la liste de contrôle.  
  
5. Faites glisser le nœud de la table enfant principale à partir de la **des Sources de données** fenêtre vers votre formulaire.  
  
     Supprimer des contrôles liés aux données (avec des étiquettes descriptives) et un outil (<xref:System.Windows.Forms.BindingNavigator>) apparaissent sur le formulaire. Un [DataSet](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter, <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant.  
  
6. Maintenant, faites glisser le nœud de la table parent principal à partir de la **des Sources de données** fenêtre directement sur le contrôle de recherche (le <xref:System.Windows.Forms.ComboBox>).  
  
     Les liaisons de recherche sont désormais établis. Consultez le tableau ci-dessous pour les propriétés spécifiques qui ont été définies sur le contrôle.  
  
    |Propriété|Explication du paramètre|  
    |--------------|----------------------------|  
    |**DataSource**|Visual Studio définit cette propriété sur le <xref:System.Windows.Forms.BindingSource> créé pour la table que vous avez fait glisser vers le contrôle (et non sur le <xref:System.Windows.Forms.BindingSource> créé en même temps que le contrôle).<br /><br /> Si vous avez besoin de faire des réglages, puis définissez ce paramètre sur le <xref:System.Windows.Forms.BindingSource> de la table contenant la colonne que vous souhaitez afficher.|  
    |**DisplayMember**|Visual Studio définit cette propriété sur la première colonne après la clé principale contenant un type de données de chaîne pour la table que vous avez fait glisser vers le contrôle.<br /><br /> Si vous avez besoin de faire des réglages, puis affectez la valeur le nom de colonne que vous souhaitez afficher.|  
    |**ValueMember**|Visual Studio définit cette propriété sur la première colonne participant à la clé principale, ou la première colonne de la table si aucune clé n'est définie.<br /><br /> Si vous avez besoin de faire des réglages, définissez à la clé primaire dans la table avec la colonne que vous souhaitez afficher.|  
    |**SelectedValue**|Visual Studio définit cette propriété sur la colonne d’origine est supprimée de la **des Sources de données** fenêtre.<br /><br /> Si vous avez besoin de faire des réglages, définissez à la colonne de clé étrangère dans la table associée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
