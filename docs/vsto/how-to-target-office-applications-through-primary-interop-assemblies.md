---
title: 'Comment : cibler les Applications Office via les assemblys PIA | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bfe02a06403621c2429dd8be965b3ab1b5c41b2c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Comment : cibler les applications Office via les assemblys PIA (Primary Interop Assembly)
  Quand vous créez un projet Office, Visual Studio ajoute automatiquement des références aux assemblys PIA (Primary Interop Assembly) Microsoft Office qui sont requises pour générer le projet Vous devez ajouter des références aux autres assemblys PIA dans les scénarios suivants :  
  
-   Vous souhaitez utiliser des fonctionnalités d'autres applications Microsoft Office dans votre projet. Par exemple, vous pouvez utiliser des fonctionnalités de Microsoft Office Excel dans un projet pour Microsoft Office Word.  
  
-   Vous souhaitez automatiser des applications Microsoft Office qui n'ont pas de projets dédiés dans Visual Studio, comme Microsoft Office Access.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Pour ajouter une référence à un assembly PIA  
  
1.  Ouvrez votre projet Office et sélectionnez le nom du projet dans **l’Explorateur de solutions**.  
  
2.  Dans le menu **Projet**, cliquez sur **Ajouter une référence**.  
  
3.  Sur le **Framework** , sélectionnez l’assembly PIA souhaité dans le **nom du composant** liste. Pour plus d’informations sur les assemblys PIA Microsoft Office disponibles, consultez [assemblys PIA Office](../vsto/office-primary-interop-assemblies.md).  
  
     Si le projet cible le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, le **incorporer les Types Interop** la référence d’assembly est définie sur **True** par défaut. Grâce à ce paramètre, votre solution ne requiert pas l'assembly PIA sur les ordinateurs des utilisateurs finaux. Pour plus d'informations, consultez [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md).  
  
    > [!NOTE]  
    >  Dans les projets Office, ajoutez toujours des références aux assemblys PIA d’Office à l’aide de la **.NET** onglet de la **ajouter une référence** boîte de dialogue plutôt que la **COM** onglet. Pour plus d’informations, consultez [Assemblys PIA (Primary Interop Assembly) Office](../vsto/office-primary-interop-assemblies.md).  
  
4.  Cliquez sur **OK**.  
  
     Le nom de l’assembly s’affiche dans le **références** dossier de **l’Explorateur de solutions**.  
  
## <a name="see-also"></a>Voir aussi  
 [Assemblys PIA Office](../vsto/office-primary-interop-assemblies.md)   
 [Écriture de Code dans les Solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Développement de Solutions Office](../vsto/developing-office-solutions.md)   
 [Guide pratique pour installer les assemblys PIA (Primary Interop Assembly) d’Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  