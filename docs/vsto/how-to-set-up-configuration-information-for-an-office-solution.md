---
title: 'Procédure : Configurer les informations de configuration pour une solution Office'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 159708bfad49e6a4a303363c6a0e9dd83b23d8e7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961258"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Procédure : Configurer les informations de configuration pour une solution Office
  Vous pouvez utiliser des fichiers de configuration pour configurer les paramètres qui sont spécifiques à vos solutions Office. Vous pouvez spécifier des paramètres tels que la stratégie de liaison d’assembly, les objets de communication à distance, paramètres de débogage et trace.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-configuration-file-to-your-office-project"></a>Pour ajouter un fichier de configuration à votre projet Office

1. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

2. Dans le **catégories** volet, cliquez sur **général**.

3. Dans le **modèles** volet, sélectionnez **fichier de Configuration d’Application**.

4. Dans le **nom** , tapez le même nom que l’assembly ainsi que l’extension *.config*. Par exemple, un fichier de configuration pour un assembly de projet Excel appelé *ExcelWorkbook1.dll* serait nommé *ExcelWorkbook1.dll.config*.

5. Cliquez sur **Ajouter**.

6. Créez votre fichier de configuration selon le schéma de fichier de configuration application. Pour plus d’informations, consultez [schéma de fichier de Configuration pour le .NET Framework](/dotnet/framework/configure-apps/file-schema/index).

   Il n’existe aucune considération particulière pour l’utilisation de fichiers de configuration avec les projets Office.

## <a name="see-also"></a>Voir aussi
- [Schéma de fichier de configuration pour le .NET Framework](/dotnet/framework/configure-apps/file-schema/index)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
- [Déployer une solution Office](../vsto/deploying-an-office-solution.md)
