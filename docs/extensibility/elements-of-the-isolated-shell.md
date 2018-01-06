---
redirect_url: shell/elements-of-the-isolated-shell
title: "Éléments du Shell isolé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b1e52963253f73c633b9b14bf64525bdb0afaeab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="elements-of-the-isolated-shell"></a>Éléments du Shell isolé
Vous pouvez modifier les paramètres du Registre, paramètres d’exécution et point d’entrée de votre application de shell isolé et son .vsct .pkgdef, les fichiers and.pkgundef application.  
  
## <a name="registry-settings"></a>Paramètres du Registre  
 Le .pkgdef et les fichiers .pkgundef modifier les paramètres du Registre pour l’application de shell isolé. Lorsque l’application est exécutée, les paramètres de Registre sont définies dans l’ordre suivant :  
  
 Lorsque l’application est exécutée, les paramètres de Registre sont définies dans l’ordre suivant :  
  
1.  La clé de Registre pour l’application est créée.  
  
2.  Le Registre est mis à jour à partir du fichier .pkgdef de l’application en définissant des entrées et des clés spécifiées.  
  
3.  Pour chaque package qui fait partie de votre application, le Registre est mis à jour à partir du fichier .pkgdef de ce package. Chaque package est défini dans le fichier .pkgdef de l’application par le \Packages $ $RootKey\\{*vsPackageGuid*} clé pour le package.  
  
4.  Le Registre est mis à jour à partir de la AppEnvConfig.pkgdef et BaseConfig.pkgdef dans les *chemin d’installation de Visual Studio SDK*\Common7\IDE\ShellExtensions\Platform active. Ces fichiers sont des parties de Visual Studio et faire partie du package redistribuable Visual Studio Shell (mode isolé).  
  
5.  Le Registre est mis à jour à partir du fichier .pkgundef de l’application en supprimant les entrées et les clés spécifiées.  
  
## <a name="run-time-settings"></a>Paramètres d’exécution  
 Lorsqu’un utilisateur démarre l’application de shell isolé, il appelle le point d’entrée de démarrage de l’interpréteur de commandes de Visual Studio. Paramètres d’application sont définis au démarrage de votre application, comme suit :  
  
1.  Le shell Visual Studio vérifie le Registre de l’application pour les clés spécifiques. Si le paramètre d’une clé est spécifié dans l’appel au point d’entrée de démarrage, cette valeur remplace la valeur dans le Registre.  
  
2.  Si le Registre, ni l’entrée point paramètre spécifie la valeur d’un paramètre, puis la valeur par défaut pour le paramètre est utilisée.  
  
 Lorsqu’un utilisateur démarre votre application à partir de la ligne de commande, tous les commutateurs de ligne de commande sont passés à l’interface de Visual Studio, qui les traite de la même manière que Devenv. Pour plus d’informations sur les commutateurs de Devenv, consultez [commutateurs de ligne de commande Devenv](../ide/reference/devenv-command-line-switches.md) et [commutateurs de ligne de commande Devenv pour le développement VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Pour plus d’informations sur la façon dont un package est inscrit pour les commutateurs de ligne de commande, consultez [Ajout des commutateurs de ligne de commande](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>Le Point d’entrée de démarrage  
 Le fichier Appenvstub.dll contient des points d’entrée pour l’accès à l’interpréteur de commandes isolé. Lorsque l’application démarre, il appelle le point d’entrée début de Appenvstub.dll.  
  
 Vous pouvez modifier le comportement de l’application en modifiant la valeur du dernier paramètre est passé au point d’entrée de démarrage. Pour plus d’informations, consultez [isolé Shell entrée de Point de paramètres (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>La barre d’outils. Fichier VSCT  
 Le fichier .vsct vous permet de spécifier les éléments d’interface utilisateur Visual Studio standards sont disponibles dans l’application. Pour plus d’informations, consultez [. Fichiers VSCT](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>La barre d’outils. Fichier de Pkgundef  
 Lorsque l’application est installée sur un ordinateur sur lequel Visual Studio est déjà installé, une copie des entrées de Registre de Visual Studio est effectuée pour l’application. Par défaut, l’application utilise des VSPackages qui sont déjà installés sur l’ordinateur. Le fichier .pkgundef vous permet d’exclure les entrées de Registre afin de supprimer des éléments spécifiques du shell Visual Studio ou des extensions de l’application. Pour plus d’informations, consultez [. Les fichiers Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Le fichier .pkgundef vous permet d’exclure les entrées de Registre afin de supprimer des éléments spécifiques du shell Visual Studio ou des extensions de l’application. Pour plus d’informations, consultez [. Les fichiers Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 L’ensemble du package GUID que vous pouvez exclure sont répertoriés dans [Package GUID de fonctionnalités Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>La barre d’outils. Fichier pkgdef  
 Le fichier .pkgdef permet de définir les entrées de Registre pour l’application qui sont définies lors de l’application est installée. Pour obtenir une description du fichier .pkgdef et une liste d’entrées de Registre par le shell Visual Studio, consultez [. Fichiers de pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Chaînes de substitution  
 Les chaînes de substitution utilisées dans les fichiers .pkgdef et .pkgundef sont répertoriés dans [Substitution chaînes utilisées dans. Pkgdef et. Les fichiers Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Autres paramètres  
 Si votre application de shell isolé dépend Microsoft.VisualStudio.GraphModel.dll, vous devez ajouter la redirection de liaison suivantes pour le fichier .config de votre application de Shell isolé :  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```