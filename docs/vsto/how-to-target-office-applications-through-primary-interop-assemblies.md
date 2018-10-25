---
title: 'Comment : applications Office de cible via les assemblys PIA'
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
ms.openlocfilehash: 576d26f039005dac3d494652f1e5127c39092a00
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863748"
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Comment : applications Office de cible via les assemblys PIA
  Quand vous créez un projet Office, Visual Studio ajoute automatiquement des références aux assemblys PIA (Primary Interop Assembly) Microsoft Office qui sont requises pour générer le projet Vous devez ajouter des références aux autres assemblys PIA dans les scénarios suivants :  
  
- Vous souhaitez utiliser des fonctionnalités d'autres applications Microsoft Office dans votre projet. Par exemple, vous pouvez utiliser des fonctionnalités de Microsoft Office Excel dans un projet pour Microsoft Office Word.  
  
- Vous souhaitez automatiser des applications Microsoft Office qui n'ont pas de projets dédiés dans Visual Studio, comme Microsoft Office Access.  
  
  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Pour ajouter une référence à un assembly PIA  
  
1.  Ouvrez votre projet Office et sélectionnez le nom du projet dans **l’Explorateur de solutions**.  
  
2.  Dans le menu **Projet**, cliquez sur **Ajouter une référence**.  
  
3.  Sur le **Framework** , sélectionnez l’assembly PIA souhaité dans le **nom du composant** liste. Pour plus d’informations sur les assemblys PIA Microsoft Office disponibles, consultez [assemblys PIA Office](../vsto/office-primary-interop-assemblies.md).  
  
     Si le projet cible le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, le **incorporer les Types Interop** a la valeur de propriété pour la référence d’assembly **True** par défaut. Grâce à ce paramètre, votre solution ne requiert pas l'assembly PIA sur les ordinateurs des utilisateurs finaux. Pour plus d’informations, consultez [conception et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md).  
  
    > [!NOTE]  
    >  Dans les projets Office, ajoutez toujours des références aux assemblys PIA Office à l’aide de la **.NET** onglet de la **ajouter une référence** boîte de dialogue plutôt que la **COM** onglet. Pour plus d’informations, consultez [assemblys PIA Office](../vsto/office-primary-interop-assemblies.md).  
  
4.  Cliquez sur **OK**.  
  
     Le nom de l’assembly s’affiche dans le **références** dossier de **l’Explorateur de solutions**.  
  
## <a name="see-also"></a>Voir aussi  
 [Assemblys PIA Office](../vsto/office-primary-interop-assemblies.md)   
 [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Développer des solutions Office](../vsto/developing-office-solutions.md)   
 [Comment : assemblys PIA Office d’installation](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  