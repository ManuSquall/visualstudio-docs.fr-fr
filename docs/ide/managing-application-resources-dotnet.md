---
title: "Gestion des ressources d’une application (.NET) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 85a03270b20b050cc5ca96f57311c98c0d9b53d1
ms.lasthandoff: 04/05/2017

---
# <a name="managing-application-resources-net"></a>Gestion des ressources d'une application (.NET)
Les fichiers de ressources sont des fichiers qui font partie d’une application, mais qui ne sont pas compilés, par exemple, des fichiers icône ou des fichiers audio. Comme ces fichiers ne font pas partie du processus de compilation, vous pouvez les modifier sans avoir à recompiler vos fichiers binaires. Si vous envisagez de localiser votre application, vous devez utiliser des fichiers de ressources pour toutes les chaînes et autres ressources qui doivent être modifiées quand vous localisez votre application.  
  
 Pour plus d’informations sur les ressources des applications de bureau .NET, consultez [Ressources dans des applications de bureau](http://msdn.microsoft.com/Library/8ad495d4-2941-40cf-bf64-e82e85825890). Pour plus d’informations sur les ressources des applications de bureau C++, consultez [Utilisation de fichiers de ressource](/cpp/windows/working-with-resource-files).  
  
 Les applications du Windows Store utilisent un autre modèle de ressources que celui des applications de bureau. Pour plus d’informations sur les ressources des applications du Windows Store, consultez [Définition des ressources d’applications](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx) sur le site web du le centre de développement Windows.  
  
## <a name="working-with-resources"></a>Utilisation de ressources  
 Dans un projet de code managé, ouvrez la fenêtre des propriétés du projet (cliquez avec le bouton droit sur le nœud de projet dans l’ **Explorateur de solutions** et sélectionnez **Propriétés**ou tapez **propriétés de projet** dans la fenêtre **Lancement rapide** , ou tapez Alt+ENTRÉE dans la fenêtre de l’ **Explorateur de solutions** ). Sélectionnez l’onglet **Ressources** . Vous pouvez ajouter un fichier .resx si votre projet n’en contient pas déjà un, ajouter et supprimer différents types de ressources, et modifier des ressources existantes.  
  
 Pour en savoir plus sur l’utilisation des ressources dans les projets C++, consultez [Guide pratique pour créer une ressource](http://msdn.microsoft.com/Library/aad44914-9145-45a3-a7d8-9de89b366716).
