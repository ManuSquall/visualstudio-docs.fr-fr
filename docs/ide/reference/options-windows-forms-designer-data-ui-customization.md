---
title: Options, Concepteur Windows Forms, personnalisation de l’interface utilisateur des données
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.Data_UI_Customization
helpviewer_keywords:
- Data UI customization options
- Options dialog box, Windows Forms Designer, Data UI Customization
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e48777a50ddf66a8e5493698fb401ff7201de03e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114692"
---
# <a name="options-dialog-box-windows-forms-designer--data-ui-customization"></a>Boîte de dialogue Options : Concepteur Windows Forms > personnalisation de l’interface utilisateur des données

Cette boîte de dialogue définit les contrôles qui apparaissent dans la liste des contrôles disponibles pour les éléments de la fenêtre Sources de données. Pour l’ouvrir, sélectionnez **Outils**  >  **options**, puis sélectionnez **Concepteur Windows Forms**  >  **Personnalisation de l’interface utilisateur des données**.

Vous pouvez sélectionner un contrôle à partir d’un élément de la fenêtre Sources de données avant de le faire glisser sur le formulaire d’une application Windows Forms. Les contrôles disponibles sont déterminés par le type de données de l’élément. Chaque type de données a une liste de contrôles associés valides tels que définis dans cette boîte de dialogue, y compris un contrôle par défaut. Lorsque vous faites glisser un élément de la fenêtre Sources de données vers un formulaire sans sélectionner de contrôle, le contrôle par défaut pour le type de données de l’élément sélectionné est ajouté au formulaire.

Personnalisez la liste des contrôles associés en activant et en désactivant les cases à cocher des contrôles disponibles pour chaque type de données. Pour ajouter un contrôle à la liste, ajoutez un contrôle qui implémente l’attribut de liaison de données <xref:System.ComponentModel.DefaultBindingPropertyAttribute> ou <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> à la Boîte à outils. Le contrôle s’affiche alors dans la liste des contrôles pour le type de données. Pour plus d’informations, consultez [Comment : ajouter des contrôles personnalisés à la fenêtre sources de données](../..//data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="data-type"></a>Type de données

Affiche la liste des types avec lesquels vous associez des contrôles. Les tables sont représentées en tant que type de données `[List]`. Les colonnes sont représentées en tant que type de données réel de la colonne dans le magasin de données sous-jacent.

## <a name="associated-controls"></a>Contrôles associés

Affiche une liste des contrôles associés au type de données sélectionné. Activez ou désactivez la case à cocher en regard du contrôle pour l’associer ou le dissocier. Les contrôles sélectionnés s’affichent dans la fenêtre Sources de données pour une colonne de base de données liée au type de données associé.

## <a name="set-default"></a>Définir la valeur par défaut

Assigne le type de contrôle sélectionné à la valeur par défaut pour le type de données sélectionné. Le contrôle par défaut apparaît comme première sélection dans le menu contextuel d’une colonne de base de données dans la fenêtre Sources de données. Lorsque vous faites glisser un élément de la fenêtre Sources de données vers un formulaire sans sélectionner de contrôle, le contrôle par défaut pour le type de données de l’élément sélectionné est ajouté au formulaire.

Un seul type de contrôle peut être assigné comme valeur par défaut pour un type de données.

## <a name="clear-default"></a>Effacer la valeur par défaut

Supprime la désignation d’un contrôle comme valeur par défaut pour le type de données sélectionné. S’il n’existe aucune valeur par défaut pour le type de données sélectionné, `[None]` apparaît comme première sélection dans le menu contextuel pour une colonne de base de données de ce type.
