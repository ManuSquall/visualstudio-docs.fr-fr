---
title: Gérer les ressources d’une application (.NET)
description: Découvrez comment gérer des fichiers de ressources d’application qui ne font pas partie du processus de compilation.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4707a3e33279ead458566bc01ed2eed8c67355cf
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596740"
---
# <a name="manage-application-resources-net"></a>Gérer les ressources d’une application (.NET)

Les fichiers de ressources sont des fichiers qui font partie d’une application, mais qui ne sont pas compilés, par exemple, des fichiers icône ou des fichiers audio. Comme ces fichiers ne font pas partie du processus de compilation, vous pouvez les modifier sans avoir à recompiler vos fichiers binaires. Si vous envisagez de localiser votre application, vous devez utiliser des fichiers de ressources pour toutes les chaînes et autres ressources qui doivent être modifiées quand vous localisez votre application.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Gestion des ressources d’application (Visual Studio pour Mac)](/visualstudio/mac/managing-app-resources).

Pour plus d’informations sur les ressources dans les applications .NET, consultez [ressources dans les applications .net](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Utiliser des ressources

Dans un projet de code managé, ouvrez la fenêtre de propriétés du projet. Vous pouvez ouvrir la fenêtre de propriétés en procédant de l’une des façons suivantes :

- Cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions** et sélectionnez **Propriétés** .
- En tapant **propriétés de projet** dans la zone de recherche **Ctrl**+**Q**
- Sélection de **ALT** + **entrée** dans **Explorateur de solutions**

Sélectionnez l’onglet **ressources** . Vous pouvez ajouter un fichier *. resx* si votre projet n’en contient pas déjà un, ajouter et supprimer différents types de ressources, et modifier des ressources existantes.

## <a name="resources-in-other-project-types"></a>Ressources dans d’autres types de projets

Les ressources dans les projets .NET sont gérées différemment par rapport aux autres types de projets. Pour plus d’informations sur les ressources dans :

- Les applications Plateforme Windows universelle (UWP), consultez [Ressources d’application et le système de gestion de ressources](/windows/uwp/app-resources/).
- Les projets C++, consultez [Utiliser des fichiers de ressources](/cpp/windows/working-with-resource-files) et [Guide pratique pour créer une ressource](/cpp/windows/how-to-create-a-resource).

## <a name="see-also"></a>Voir aussi

- [Ressources dans les applications .NET (.NET Framework)](/dotnet/framework/resources/index)
- [Gestion des ressources d’application (Visual Studio pour Mac)](/visualstudio/mac/managing-app-resources)
