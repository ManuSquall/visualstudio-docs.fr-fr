---
title: Boîte à outils, onglet Données | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Data tab
- Data tab, Toolbox
- data [Visual Studio], Toolbox
ms.assetid: 2ae38b2a-29d2-461c-a67d-29dad274bf45
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9349745eeee24f2f8b1e62eb2b01bd75273c86d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658594"
---
# <a name="toolbox-data-tab"></a>Boîte à outils, onglet Données
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Affiche des objets de données que vous pouvez ajouter à un formulaire et à des composants. L’onglet **Données** de la **boîte à outils** apparaît quand vous créez un projet associé à un concepteur. La **boîte à outils** apparaît par défaut dans l’environnement de développement intégré Visual Studio ; si vous devez afficher la **boîte à outils**, sélectionnez **Boîte à outils** dans le menu **Affichage**.

> [!TIP]
> L’exécution de l’Assistant Configuration de source de données crée et configure automatiquement la plupart des éléments de données. Pour plus d’informations, voir [Créer des applications de données avec Visual Studio](https://msdn.microsoft.com/28edce21-220a-484c-b461-a75b0232d293).

## <a name="ui-element-list"></a>Liste des éléments de l'interface utilisateur
 Pour accéder directement à la page de référence .NET Framework d’un composant, appuyez sur **F1** avec le pointeur placé sur l’élément dans la **boîte à outils** ou sur le composant dans la barre d’état du concepteur.

|Nom|Description|
|----------|-----------------|
|<xref:System.Data.DataSet>|Ajoute une instance d’un dataset typé ou non typé au formulaire ou composant. Quand vous faites glisser cet objet dans un concepteur, il affiche une boîte de dialogue qui permet de sélectionner une classe de dataset typée existante ou de spécifier que vous souhaitez créer un dataset vide et non typé. **Remarque :** N’utilisez pas l’objet <xref:System.Data.DataSet> de la **boîte à outils** pour créer un schéma et une classe de dataset typés. Pour plus d’informations, consultez [Créer et configurer des datasets](../../data-tools/create-and-configure-datasets-in-visual-studio.md).|
|<xref:System.Windows.Forms.DataGridView>|Offre un moyen puissant et souple d’afficher des données sous forme de tableau.|
|<xref:System.Windows.Forms.BindingSource>|Simplifie le processus de liaison des contrôles à une source de données sous-jacente.|
|<xref:System.Windows.Forms.BindingNavigator>|Représente l'interface utilisateur de navigation et manipulation pour les contrôles d'un formulaire liés aux données.|

## <a name="see-also"></a>Voir aussi
 Les [procédures pas à pas relatives aux données](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4) [lient des contrôles Windows Forms à des données dans Visual Studio](../../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [préparation de votre application pour recevoir](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) des [contrôles de liaison de données à des données dans Visual Studio](../../data-tools/bind-controls-to-data-in-visual-studio.md) [validation des données](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)