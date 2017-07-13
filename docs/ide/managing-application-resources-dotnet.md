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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 5cb2e044f5c55881adade6d3022fc453360a2e9c
ms.contentlocale: fr-fr
ms.lasthandoff: 05/30/2017

---
# Gestion des ressources d'une application (.NET)
<a id="managing-application-resources-net" class="xliff"></a>
Les fichiers de ressources sont des fichiers qui font partie d’une application, mais qui ne sont pas compilés, par exemple, des fichiers icône ou des fichiers audio. Comme ces fichiers ne font pas partie du processus de compilation, vous pouvez les modifier sans avoir à recompiler vos fichiers binaires. Si vous envisagez de localiser votre application, vous devez utiliser des fichiers de ressources pour toutes les chaînes et autres ressources qui doivent être modifiées quand vous localisez votre application.  
  
 Pour plus d’informations sur les ressources des applications de bureau .NET, consultez [Ressources dans des applications de bureau](/dotnet/framework/resources/index). Pour plus d’informations sur les ressources des applications de bureau C++, consultez [Working with Resource Files](/cpp/windows/working-with-resource-files).  
  
 Les applications du Windows Store utilisent un autre modèle de ressources que celui des applications de bureau. Pour plus d’informations sur les ressources des applications du Windows Store, consultez [Définition des ressources d’applications](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx) sur le site web du le centre de développement Windows.  
  
## Utilisation de ressources
<a id="working-with-resources" class="xliff"></a>  
 Dans un projet de code managé, ouvrez la fenêtre des propriétés du projet (cliquez avec le bouton droit sur le nœud de projet dans l’ **Explorateur de solutions** et sélectionnez **Propriétés**ou tapez **propriétés de projet** dans la fenêtre **Lancement rapide** , ou tapez Alt+ENTRÉE dans la fenêtre de l’ **Explorateur de solutions** ). Sélectionnez l’onglet **Ressources** . Vous pouvez ajouter un fichier .resx si votre projet n’en contient pas déjà un, ajouter et supprimer différents types de ressources, et modifier des ressources existantes.  
  
 Pour en savoir plus sur l’utilisation des ressources dans les projets C++, consultez [Guide pratique pour créer une ressource](/cpp/windows/how-to-create-a-resource).
