---
title: 'Procédure : Ajouter ou supprimer des espaces de noms importés (Visual Basic) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1eb88a5baa09256aa58d3c62b926047df01b32f2
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700990"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Procédure : Ajouter ou supprimer des espaces de noms importés (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’importation d’un espace de noms vous permet d’utiliser des éléments issus de cet espace de noms dans votre code sans avoir à qualifier complètement l’élément. Par exemple, pour accéder à la méthode `Create` dans la classe `System.Messaging.MessageQueue`, vous pouvez importer l’espace de noms `System.Messaging` et simplement référencer l’élément dont vous avez besoin dans le code sous la forme `MessageQueue.Create`.  
  
 Les espaces de noms importés sont gérés dans la page **Références** du **Concepteur de projet**. Les importations que vous spécifiez dans cette boîte de dialogue sont passées directement au compilateur (`/imports`) et s’appliquent à tous les fichiers de votre projet. Utilisez l’instruction `Imports` pour utiliser un espace de noms dans un fichier de code source unique.  
  
### <a name="to-add-an-imported-namespace"></a>Pour ajouter un espace de noms importé  
  
1. Dans l’**Explorateur de solutions**, double-cliquez sur le nœud **Mon projet** du projet.  
  
2. Dans le **Concepteur de projet**, cliquez sur l’onglet **Références**.  
  
3. Dans la liste **Espaces de noms importés**, cochez la case de l’espace de noms que vous souhaitez ajouter.  
  
    > [!NOTE]
    > Pour pouvoir être importé, l’espace de noms doit être dans un composant référencé. Si l’espace de noms n’apparaît pas dans la liste, vous devrez ajouter une référence au composant qui le contient. Pour plus d’informations, consultez [NIB Comment : Ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter référence](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
### <a name="to-remove-an-imported-namespace"></a>Pour supprimer un espace de noms importé  
  
1. Dans l’**Explorateur de solutions**, double-cliquez sur le nœud **Mon projet** du projet.  
  
2. Dans le **Concepteur de projet**, cliquez sur l’onglet **Références**.  
  
3. Dans la liste **Espaces de noms importés**, décochez la case de l’espace de noms que vous souhaitez supprimer.  
  
## <a name="user-imports"></a>Importations utilisateur  
 Les importations utilisateur vous permettent d’importer une classe spécifique d’un espace de noms plutôt que l’espace de noms complet. Par exemple, votre application peut avoir une importation pour l’espace de noms `Systems.Diagnostics`, mais la seule classe de cet espace de noms qui vous intéresse est la classe `Debug`. Vous pouvez définir `System.Diagnostics.Debug` en tant qu’importation utilisateur, puis supprimer l’importation de `System.Diagnostics`.  
  
 Si vous changez d’avis ultérieurement et concluez que vous avez véritablement besoin de la classe `EventLog`, vous pouvez entrer `System.Diagnostics.EventLog` en tant qu’importation utilisateur et remplacer `System.Diagnostics.Debug` en utilisant la fonctionnalité de mise à jour.  
  
#### <a name="to-add-a-user-import"></a>Pour ajouter une importation utilisateur  
  
1. Dans l’**Explorateur de solutions**, double-cliquez sur le nœud **Mon projet** du projet.  
  
2. Dans le **Concepteur de projet**, cliquez sur l’onglet **Références**.  
  
3. Dans la zone de texte située sous la liste **Espaces de noms importés**, entrez le nom complet de l’espace de noms que vous souhaitez importer, notamment l’espace de noms racine.  
  
4. Cliquez sur le bouton **Ajouter une importation utilisateur** pour ajouter l’espace de noms à la liste **Espaces de noms importés**.  
  
    > [!NOTE]
    > Le bouton **Ajouter une importation utilisateur** est désactivé si l’espace de noms figure déjà dans la liste. Vous ne pouvez pas ajouter deux fois une même importation.  
  
#### <a name="to-update-a-user-import"></a>Pour mettre à jour une importation utilisateur  
  
1. Dans l’**Explorateur de solutions**, double-cliquez sur le nœud **Mon projet** du projet.  
  
2. Dans le **Concepteur de projet**, cliquez sur l’onglet **Références**.  
  
3. Dans la liste **Espaces de noms importés**, sélectionnez l’espace de noms que vous souhaitez changer.  
  
4. Dans la zone de texte située sous la liste **Espaces de noms importés**, entrez le nom du nouvel espace de noms.  
  
5. Cliquez sur le bouton **Mettre à jour l’importation utilisateur** pour mettre à jour l’espace de noms dans la liste **Espaces de noms importés**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)
