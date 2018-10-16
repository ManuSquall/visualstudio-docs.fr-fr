---
title: Éléments du Shell isolé | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c051425f2d3ae131362c2d95494ed0edbef5353e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246049"
---
# <a name="elements-of-the-isolated-shell"></a>Éléments du Shell isolé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez modifier les paramètres du Registre, paramètres d’exécution et application point d’entrée de votre application de shell isolé et son .vsct .pkgdef, les fichiers and.pkgundef.  
  
## <a name="registry-settings"></a>Paramètres du Registre  
 Le .pkgdef et .pkgundef fichiers modifier les paramètres du Registre pour l’application de shell isolé. Lorsque l’application est exécutée, les paramètres du Registre sont définies dans l’ordre suivant :  
  
 Lorsque l’application est exécutée, les paramètres du Registre sont définies dans l’ordre suivant :  
  
1.  La clé de Registre pour l’application est créée.  
  
2.  Le Registre est mis à jour à partir du fichier .pkgdef de l’application en définissant des entrées et des clés spécifiées.  
  
3.  Pour chaque package fait partie de votre application, le Registre est mis à jour à partir du fichier .pkgdef de ce package. Chaque package est défini dans le fichier .pkgdef de l’application par le \Packages $ $RootKey\\{*vsPackageGuid*} clés pour le package.  
  
4.  Le Registre est mis à jour à partir de la AppEnvConfig.pkgdef et BaseConfig.pkgdef dans le *chemin d’installation de Visual Studio SDK*\Common7\IDE\ShellExtensions\Platform directory. Ces fichiers sont la partie de Visual Studio et également partie du package redistribuable Visual Studio Shell (mode isolé).  
  
5.  Le Registre est mis à jour à partir du fichier .pkgundef de l’application en supprimant les entrées et les clés spécifiées.  
  
## <a name="run-time-settings"></a>Paramètres d’exécution  
 Quand un utilisateur démarre l’application de shell isolé, il appelle le point d’entrée de démarrage de l’interpréteur de commandes de Visual Studio. Paramètres d’application sont définies lorsque votre application démarre, comme suit :  
  
1.  Le shell Visual Studio vérifie le Registre de l’application pour des clés spécifiques. Si le paramètre d’une clé est spécifié dans l’appel au point d’entrée de démarrage, cette valeur remplace la valeur dans le Registre.  
  
2.  Si ni le Registre, ni l’entrée point paramètre spécifie la valeur d’un paramètre, puis la valeur par défaut pour le paramètre est utilisée.  
  
 Quand un utilisateur démarre votre application à partir de la ligne de commande, tous les commutateurs de ligne de commande sont passés à l’interpréteur de commandes de Visual Studio, qui les traite de la même manière que Devenv. Pour plus d’informations sur les commutateurs de Devenv, consultez [commutateurs de ligne de commande Devenv](../ide/reference/devenv-command-line-switches.md) et [commutateurs de ligne de commande de Devenv pour le développement VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Pour plus d’informations sur la façon dont un package s’inscrit pour les commutateurs de ligne de commande, consultez [Ajout des commutateurs de ligne de commande](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>Le Point d’entrée de démarrage  
 Le fichier Appenvstub.dll contient des points d’entrée pour accéder à l’interpréteur de commandes isolé. Lorsque l’application démarre, il appelle le point d’entrée début de Appenvstub.dll.  
  
 Vous pouvez modifier le comportement de l’application en modifiant la valeur du dernier paramètre est transmis au point d’entrée de démarrage. Pour plus d’informations, consultez [isolé Shell entrée Point de paramètres (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>La barre d’outils. Fichier VSCT  
 Le fichier .vsct vous permet de spécifier les éléments d’interface utilisateur Visual Studio standards sont disponibles dans l’application. Pour plus d’informations, consultez [. Fichiers VSCT](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>La barre d’outils. Fichier de Pkgundef  
 Lorsque l’application est installée sur un ordinateur sur lequel Visual Studio est déjà installé, une copie des entrées du Registre de Visual Studio est effectuée pour l’application. Par défaut, l’application utilise les VSPackages sont déjà installés sur l’ordinateur. Le fichier .pkgundef vous permet d’exclure les entrées de Registre afin de supprimer des éléments spécifiques de l’interpréteur de commandes de Visual Studio ou les extensions à partir de l’application. Pour plus d’informations, consultez [. Les fichiers Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Le fichier .pkgundef vous permet d’exclure les entrées de Registre afin de supprimer des éléments spécifiques de l’interpréteur de commandes de Visual Studio ou les extensions à partir de l’application. Pour plus d’informations, consultez [. Les fichiers Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 L’ensemble du package GUID que vous pouvez exclure sont répertoriés dans [Package GUID de fonctionnalités de Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>La barre d’outils. Fichier pkgdef  
 Le fichier .pkgdef vous permet de définir les entrées de Registre pour l’application qui sont définies lors de l’application est installée. Pour une description du fichier .pkgdef et une liste d’entrées de Registre qui utilise le shell Visual Studio, consultez [. Fichiers pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Chaînes de substitution  
 Les chaînes de substitution utilisés dans les fichiers .pkgdef et .pkgundef sont répertoriés dans [Substitution chaînes utilisées dans. Pkgdef et. Les fichiers Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Autres paramètres  
 Si votre application de shell isolé dépend Microsoft.VisualStudio.GraphModel.dll, vous devez ajouter la redirection de liaison suivantes au fichier .config de votre application de Shell isolé :  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```

