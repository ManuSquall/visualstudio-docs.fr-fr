---
title: Gestion des ressources d’une application (.NET) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: efe2b176db9f6f22f9e38775d5fc8acad87655ba
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651386"
---
# <a name="managing-application-resources-net"></a>Gestion des ressources d'une application (.NET)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les fichiers de ressources sont des fichiers qui font partie d’une application, mais qui ne sont pas compilés, par exemple, des fichiers icône ou des fichiers audio. Comme ces fichiers ne font pas partie du processus de compilation, vous pouvez les modifier sans avoir à recompiler vos fichiers binaires. Si vous envisagez de localiser votre application, vous devez utiliser des fichiers de ressources pour toutes les chaînes et autres ressources qui doivent être modifiées quand vous localisez votre application.

 Pour plus d’informations sur les ressources des applications de bureau .NET, consultez [Ressources dans des applications de bureau](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890). Pour plus d’informations sur les ressources des applications de bureau C++, consultez [Working with Resource Files](https://msdn.microsoft.com/library/2699a539-b369-4b78-80f0-df03eb7b6780).

 Les applications du Windows Store utilisent un autre modèle de ressources que celui des applications de bureau. Pour plus d’informations sur les ressources des applications du Windows Store, consultez [Définition des ressources d’applications](https://msdn.microsoft.com/library/windows/apps/hh465228.aspx) sur le site web du le centre de développement Windows.

## <a name="working-with-resources"></a>Utilisation de ressources
 Dans un projet de code managé, ouvrez la fenêtre des propriétés du projet (cliquez avec le bouton droit sur le nœud de projet dans l’ **Explorateur de solutions** et sélectionnez **Propriétés**ou tapez **propriétés de projet** dans la fenêtre **Lancement rapide** , ou tapez Alt+ENTRÉE dans la fenêtre de l’ **Explorateur de solutions** ). Sélectionnez l’onglet **ressources** . Vous pouvez ajouter un fichier. resx si votre projet n’en contient pas déjà un, ajouter et supprimer différents types de ressources, et modifier des ressources existantes.

 Pour en savoir plus sur l’utilisation des ressources dans les projets C++, consultez [Guide pratique pour créer une ressource](https://msdn.microsoft.com/library/aad44914-9145-45a3-a7d8-9de89b366716).
