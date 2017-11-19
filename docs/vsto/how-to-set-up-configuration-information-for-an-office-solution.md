---
title: "Comment : définir les informations de Configuration pour une Solution Office | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
ms.assetid: f123838f-957a-4cf5-acc0-0cc0f4c2aea2
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a8c2e0a904ad3cdbef3e70072d263cc26274de52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Comment : configurer les informations de configuration d'une solution Office
  Vous pouvez utiliser des fichiers de configuration pour configurer les paramètres qui sont spécifiques à vos solutions Office. Vous pouvez spécifier les paramètres de stratégie de liaison d’assembly, les objets de communication à distance, débogage et des paramètres de trace.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-configuration-file-to-your-office-project"></a>Pour ajouter un fichier de configuration à votre projet Office  
  
1.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
2.  Dans le **catégories** volet, cliquez sur **général**.  
  
3.  Dans le **modèles** volet, sélectionnez **fichier de Configuration de l’Application**.  
  
4.  Dans le **nom** , tapez le même nom que l’assembly avec l’extension .config. Par exemple, un fichier de configuration pour un assembly de projet Excel appelé ExcelWorkbook1.dll serait nommé ExcelWorkbook1.dll.config.  
  
5.  Cliquez sur **Ajouter**.  
  
6.  Créez votre fichier de configuration selon le schéma de fichier de configuration application. Pour plus d’informations, consultez [schéma de fichier de Configuration pour le .NET Framework](/dotnet/framework/configure-apps/file-schema/index).  
  
 Il n’existe aucune considération particulière pour l’utilisation de fichiers de configuration avec les projets Office.  
  
## <a name="see-also"></a>Voir aussi  
 [Schéma de fichier de configuration pour le .NET Framework](/dotnet/framework/configure-apps/file-schema/index)   
 [Conception et création de Solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Déploiement d’une solution Office](../vsto/deploying-an-office-solution.md)  
  
  