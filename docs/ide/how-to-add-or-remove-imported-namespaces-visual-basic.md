---
title: "Guide pratique pour ajouter ou supprimer des espaces de noms importés (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d2f4eba36e9069a35cf279ccf1c78f72a51d77a1
ms.openlocfilehash: f512673808ae3fab2fdcca39b58f77ca5df93e05
ms.contentlocale: fr-fr
ms.lasthandoff: 06/23/2017

---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Guide pratique pour ajouter ou supprimer des espaces de noms importés (Visual Basic)
L’importation d’un espace de noms vous permet d’utiliser des éléments issus de cet espace de noms dans votre code sans avoir à qualifier complètement l’élément. Par exemple, pour accéder à la méthode `Create` dans la classe `System.Messaging.MessageQueue`, vous pouvez importer l’espace de noms `System.Messaging` et simplement référencer l’élément dont vous avez besoin dans le code sous la forme `MessageQueue.Create`.  

 Les espaces de noms importés sont gérés dans la page **Références** du **Concepteur de projet**. Les importations que vous spécifiez dans cette boîte de dialogue sont passées directement au compilateur (`/imports`) et s’appliquent à tous les fichiers de votre projet. Utilisez l’instruction `Imports` pour utiliser un espace de noms dans un fichier de code source unique.  

### <a name="to-add-an-imported-namespace"></a>Pour ajouter un espace de noms importé  

1.  Dans l’**Explorateur de solutions**, double-cliquez sur le nœud **Mon projet** du projet.  

2.  Dans le **Concepteur de projet**, cliquez sur l’onglet **Références**.  

3.  Dans la liste **Espaces de noms importés**, cochez la case de l’espace de noms que vous souhaitez ajouter.  

    > [!NOTE]
    >  Pour pouvoir être importé, l’espace de noms doit être dans un composant référencé. Si l’espace de noms n’apparaît pas dans la liste, vous devrez ajouter une référence au composant qui le contient. Pour plus d’informations, consultez [Gestion des références dans un projet](managing-references-in-a-project.md).  
  
### <a name="to-remove-an-imported-namespace"></a>Pour supprimer un espace de noms importé  

1.  Dans l’**Explorateur de solutions**, double-cliquez sur le nœud **Mon projet** du projet.  

2.  Dans le **Concepteur de projet**, cliquez sur l’onglet **Références**.  

3.  Dans la liste **Espaces de noms importés**, décochez la case de l’espace de noms que vous souhaitez supprimer.  

## <a name="user-imports"></a>Importations utilisateur  
 Les importations utilisateur vous permettent d’importer une classe spécifique d’un espace de noms plutôt que l’espace de noms complet. Par exemple, votre application peut avoir une importation pour l’espace de noms `Systems.Diagnostics`, mais la seule classe de cet espace de noms qui vous intéresse est la classe `Debug`. Vous pouvez définir `System.Diagnostics.Debug` en tant qu’importation utilisateur, puis supprimer l’importation de `System.Diagnostics`.  

 Si vous changez d’avis ultérieurement et concluez que vous avez véritablement besoin de la classe `EventLog`, vous pouvez entrer `System.Diagnostics.EventLog` en tant qu’importation utilisateur et remplacer `System.Diagnostics.Debug` en utilisant la fonctionnalité de mise à jour.  

#### <a name="to-add-a-user-import"></a>Pour ajouter une importation utilisateur  

1.  Dans l’**Explorateur de solutions**, double-cliquez sur le nœud **Mon projet** du projet.  

2.  Dans le **Concepteur de projet**, cliquez sur l’onglet **Références**.  

3.  Dans la zone de texte située sous la liste **Espaces de noms importés**, entrez le nom complet de l’espace de noms que vous souhaitez importer, notamment l’espace de noms racine.  

4.  Cliquez sur le bouton **Ajouter une importation utilisateur** pour ajouter l’espace de noms à la liste **Espaces de noms importés**.  

    > [!NOTE]
    >  Le bouton **Ajouter une importation utilisateur** est désactivé si l’espace de noms figure déjà dans la liste. Vous ne pouvez pas ajouter deux fois une même importation.  

#### <a name="to-update-a-user-import"></a>Pour mettre à jour une importation utilisateur  

1.  Dans l’**Explorateur de solutions**, double-cliquez sur le nœud **Mon projet** du projet.  

2.  Dans le **Concepteur de projet**, cliquez sur l’onglet **Références**.  

3.  Dans la liste **Espaces de noms importés**, sélectionnez l’espace de noms que vous souhaitez changer.  

4.  Dans la zone de texte située sous la liste **Espaces de noms importés**, entrez le nom du nouvel espace de noms.  

5.  Cliquez sur le bouton **Mettre à jour l’importation utilisateur** pour mettre à jour l’espace de noms dans la liste **Espaces de noms importés**.  

## <a name="see-also"></a>Voir aussi  
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)

