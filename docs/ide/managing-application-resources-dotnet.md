---
title: Gérer les ressources d’une application (.NET)
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
ms.openlocfilehash: e53c3701e31733c54869c71820956d674ed4fb8b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593692"
---
# <a name="manage-application-resources-net"></a>Gérer les ressources d’une application (.NET)

Les fichiers de ressources sont des fichiers qui font partie d’une application, mais qui ne sont pas compilés, par exemple, des fichiers icône ou des fichiers audio. Comme ces fichiers ne font pas partie du processus de compilation, vous pouvez les modifier sans avoir à recompiler vos fichiers binaires. Si vous envisagez de localiser votre application, vous devez utiliser des fichiers de ressources pour toutes les chaînes et autres ressources qui doivent être modifiées quand vous localisez votre application.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Gestion des ressources d’application (Visual Studio pour Mac)](/visualstudio/mac/managing-app-resources).

Pour plus d’informations sur les ressources dans les applications de bureau .NET, voir [Ressources dans les applications de bureau](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Utiliser des ressources

Dans un projet de code managé, ouvrez la fenêtre de propriétés du projet. Vous pouvez ouvrir la fenêtre de propriétés en procédant de l’une des façons suivantes :

- En cliquant à droite sur le nœud du projet dans **Solution Explorer** et en sélectionnant les **propriétés**
- En tapant **propriétés de projet** dans la zone de recherche **Ctrl**+**Q**
- Choisir **Alt**+**Entrez** dans **Solution Explorer**

Sélectionnez l’onglet **Ressources.** Vous pouvez ajouter un fichier *.resx* si votre projet ne contient pas déjà un, ajouter et supprimer différents types de ressources, et modifier les ressources existantes.

## <a name="resources-in-other-project-types"></a>Ressources dans d’autres types de projets

Les ressources dans les projets .NET sont gérées différemment par rapport aux autres types de projets. Pour plus d’informations sur les ressources dans :

- Les applications Plateforme Windows universelle (UWP), consultez [Ressources d’application et le système de gestion de ressources](/windows/uwp/app-resources/).
- Les projets C++, consultez [Utiliser des fichiers de ressources](/cpp/windows/working-with-resource-files) et [Guide pratique pour créer une ressource](/cpp/windows/how-to-create-a-resource).

## <a name="see-also"></a>Voir aussi

- [Ressources dans les applications de bureau (.NET Framework)](/dotnet/framework/resources/index)
- [Gestion des ressources d’application (Visual Studio pour Mac)](/visualstudio/mac/managing-app-resources)
