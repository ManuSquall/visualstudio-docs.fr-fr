---
title: "Gestion des ressources d’une application (.NET) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2006f565edbca8a859cd2c155645e47e083b5528
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2018
---
# <a name="managing-application-resources-net"></a>Gestion des ressources d’une application (.NET)

Les fichiers de ressources sont des fichiers qui font partie d’une application, mais qui ne sont pas compilés, par exemple, des fichiers icône ou des fichiers audio. Comme ces fichiers ne font pas partie du processus de compilation, vous pouvez les modifier sans avoir à recompiler vos fichiers binaires. Si vous envisagez de localiser votre application, vous devez utiliser des fichiers de ressources pour toutes les chaînes et autres ressources qui doivent être modifiées quand vous localisez votre application.

Pour plus d’informations sur les ressources des applications de bureau .NET, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index).

## <a name="working-with-resources"></a>Utilisation de ressources

Dans un projet de code managé, ouvrez la fenêtre de propriétés du projet. Vous pouvez ouvrir la fenêtre de propriétés en procédant de l’une des façons suivantes :

- en cliquant avec le bouton droit sur le nœud du projet dans l’**Explorateur de solutions**, puis sélectionnant **Propriétés**
- En tapant « propriétés de projet » dans la fenêtre **Lancement rapide**.
- En choisissant **Alt**+**Entrée** dans la fenêtre **Explorateur de solutions**.

Sélectionnez l’onglet **Ressources** . Vous pouvez ajouter un fichier .resx si votre projet n’en contient pas déjà un, ajouter et supprimer différents types de ressources, et modifier des ressources existantes.

## <a name="resources-in-other-project-types"></a>Ressources dans d’autres types de projets

Les ressources dans les projets .NET sont gérées différemment par rapport aux autres types de projets. Pour plus d’informations sur les ressources dans :

- Les applications Plateforme Windows universelle (UWP), consultez [Ressources d’application et le système de gestion de ressources](/windows/uwp/app-resources/).
- Les projets C++, consultez [Utilisation des fichiers de ressources](/cpp/windows/working-with-resource-files) et [Guide pratique pour créer une ressource](/cpp/windows/how-to-create-a-resource).

## <a name="see-also"></a>Voir aussi

[Ressources dans les applications de bureau (.NET Framework)](/dotnet/framework/resources/index)