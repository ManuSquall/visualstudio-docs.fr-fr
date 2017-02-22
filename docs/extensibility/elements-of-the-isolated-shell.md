---
title: "&#201;l&#233;ments du Shell isol&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Shell Visual Studio, en mode isolé"
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# &#201;l&#233;ments du Shell isol&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez modifier les paramètres du Registre, paramètres d’exécution et point d’entrée de votre application shell isolé et ses .vsct .pkgdef, les fichiers and.pkgundef application.  
  
## Paramètres du Registre  
 Le .pkgdef et les fichiers .pkgundef modifier les paramètres du Registre pour l’application shell isolé. Lorsque l’application est exécutée, les paramètres du Registre sont définies dans l’ordre suivant :  
  
 Lorsque l’application est exécutée, les paramètres du Registre sont définies dans l’ordre suivant :  
  
1.  La clé de Registre pour l’application est créée.  
  
2.  Le Registre est mis à jour à partir du fichier .pkgdef de l’application en définissant des entrées et des clés spécifiées.  
  
3.  Pour chaque package qui fait partie de votre application, le Registre est mis à jour à partir du fichier .pkgdef de ce package. Chaque package est défini dans le fichier .pkgdef de l’application par le \\Packages\\$ $RootKey {*vsPackageGuid*} clé pour le package.  
  
4.  Le Registre est mis à jour à partir de la AppEnvConfig.pkgdef et BaseConfig.pkgdef dans les *chemin d’installation de Visual Studio SDK*\\Common7\\IDE\\ShellExtensions\\Platform active. Ces fichiers sont inclus dans Visual Studio et également partie du package redistribuable Visual Studio Shell \(mode isolé\).  
  
5.  Le Registre est mis à jour à partir du fichier .pkgundef de l’application en supprimant les entrées et les clés spécifiées.  
  
## Paramètres d’exécution  
 Lorsqu’un utilisateur lance l’application shell isolé, il appelle le point d’entrée de démarrage de l’interpréteur de commandes de Visual Studio. Paramètres d’application sont définies lorsque votre application démarre, comme suit :  
  
1.  Le shell Visual Studio vérifie le Registre de l’application pour les clés spécifiques. Si le paramètre d’une clé est spécifié dans l’appel vers le point d’entrée de démarrage, cette valeur remplace la valeur dans le Registre.  
  
2.  Si le Registre, ni l’entrée du point paramètre spécifie la valeur d’un paramètre, la valeur par défaut pour le paramètre est utilisée.  
  
 Lorsqu’un utilisateur lance votre application à partir de la ligne de commande, tous les commutateurs de ligne de commande sont passés à l’interface de Visual Studio, qui les traite de la même manière que Devenv. Pour plus d’informations sur les commutateurs de Devenv, consultez [Commutateurs de la ligne de commande de Devenv](../ide/reference/devenv-command-line-switches.md) et [Commutateurs de ligne de commande devenv pour le développement VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Pour plus d’informations sur la façon dont un package enregistre pour les commutateurs de ligne de commande, consultez la page [Ajout de commutateurs de ligne de commande](../extensibility/adding-command-line-switches.md).  
  
## Le Point d’entrée de démarrage  
 Le fichier Appenvstub.dll contient des points d’entrée pour accéder à l’interface isolé. Lorsque l’application démarre, il appelle le point d’entrée début de Appenvstub.dll.  
  
 Vous pouvez modifier le comportement de l’application en modifiant la valeur du dernier paramètre qui est transmis au point d’entrée de démarrage. Pour plus d'informations, consultez [Paramètres du Point d'entrée Shell isolé \(C\+\+\)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## La barre d’outils. Fichier VSCT  
 Le fichier .vsct vous permet de spécifier les éléments d’interface utilisateur de Visual Studio standards sont disponibles dans l’application. Pour plus d'informations, consultez [. Fichiers VSCT](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## La barre d’outils. Fichier de Pkgundef  
 Lorsque l’application est installée sur un ordinateur sur lequel Visual Studio est déjà installé, une copie des entrées de Registre Visual Studio est effectuée pour l’application. Par défaut, l’application utilise les VSPackages sont déjà installés sur l’ordinateur. Le fichier .pkgundef vous permet d’exclure les entrées de Registre afin de supprimer des éléments spécifiques de l’interpréteur de commandes de Visual Studio ou les extensions de l’application. Pour plus d'informations, consultez [. Fichiers Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Le fichier .pkgundef vous permet d’exclure les entrées de Registre afin de supprimer des éléments spécifiques de l’interpréteur de commandes de Visual Studio ou les extensions de l’application. Pour plus d'informations, consultez [. Fichiers Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 L’ensemble du package GUID que vous pouvez exclure répertoriés dans [GUID du package de fonctionnalités de Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
## La barre d’outils. Fichier de pkgdef  
 Le fichier .pkgdef vous permet de définir les entrées de Registre pour l’application qui sont définies lors de l’application est installée. Pour obtenir une description du fichier .pkgdef et une liste d’entrées de Registre qui utilise le shell Visual Studio, consultez [. Fichiers pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## Chaînes de substitution  
 Les chaînes de substitution utilisées dans les fichiers .pkgdef et .pkgundef sont répertoriés dans [Chaînes de substitution utilisées dans. Pkgdef et. Fichiers Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## Autres paramètres  
 Si votre application shell isolé dépend de Microsoft.VisualStudio.GraphModel.dll, vous devez ajouter la redirection de liaison suivantes au fichier .config de votre application Shell isolé :  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```