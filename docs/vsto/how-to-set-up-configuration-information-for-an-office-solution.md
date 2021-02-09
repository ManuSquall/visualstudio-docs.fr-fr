---
title: Configurer les informations de configuration d’une solution Office
description: Découvrez comment vous pouvez utiliser des fichiers de configuration pour configurer des paramètres spécifiques à vos solutions Microsoft Office.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: da3a08ad9b3f6c78a10891e7d8ef2093ab46305d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927702"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Comment : configurer les informations de configuration d’une solution Office
  Vous pouvez utiliser des fichiers de configuration pour configurer des paramètres spécifiques à vos solutions Office. Vous pouvez spécifier des paramètres tels que la stratégie de liaison d’assembly, les objets de communication à distance, le débogage et les paramètres de trace.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-configuration-file-to-your-office-project"></a>Pour ajouter un fichier de configuration à votre projet Office

1. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

2. Dans le volet **catégories** , cliquez sur **général**.

3. Dans le volet **modèles** , sélectionnez **fichier de configuration** de l’application.

4. Dans la zone **nom** , tapez le même nom que l’assembly et l’extension *. config*. Par exemple, un fichier de configuration pour un assembly de projet Excel appelé *ExcelWorkbook1.dll* serait nommé *ExcelWorkbook1.dll.config*.

5. Cliquez sur **Add**.

6. Créez votre fichier de configuration selon le schéma du fichier de configuration de l’application. Pour plus d’informations, consultez [schéma du fichier de configuration pour le .NET Framework](/dotnet/framework/configure-apps/file-schema/index).

   Il n’existe aucune considération particulière pour l’utilisation de fichiers de configuration avec des projets Office.

## <a name="see-also"></a>Voir aussi
- [Schéma du fichier de configuration pour le .NET Framework](/dotnet/framework/configure-apps/file-schema/index)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
- [Déployer une solution Office](../vsto/deploying-an-office-solution.md)
