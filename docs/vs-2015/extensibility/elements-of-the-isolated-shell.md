---
title: Éléments de l’interpréteur de commandes isolé | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a95b7da718f050357f6ecd79c90c389dd6085d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204601"
---
# <a name="elements-of-the-isolated-shell"></a>Éléments du Shell isolé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez modifier les paramètres du Registre, les paramètres d’exécution et le point d’entrée de l’application de votre application d’interpréteur de commandes isolé, ainsi que ses fichiers. vsct,. pkgdef et. pkgundef.  
  
## <a name="registry-settings"></a>Paramètres du Registre  
 Les fichiers. pkgdef et. pkgundef modifient les paramètres du Registre pour l’application Shell isolée. Lorsque l’application est exécutée, les paramètres du Registre sont définis dans l’ordre suivant :  
  
 Lorsque l’application est exécutée, les paramètres du Registre sont définis dans l’ordre suivant :  
  
1. La clé de registre de l’application est créée.  
  
2. Le Registre est mis à jour à partir du fichier. pkgdef de l’application en définissant les clés et les entrées spécifiées.  
  
3. Pour chaque package qui fait partie de votre application, le Registre est mis à jour à partir du fichier. pkgdef de ce package. Chaque package est défini dans le fichier. pkgdef de l’application par la clé $RootKey $ \Packages \\ {*vsPackageGuid*} pour le package.  
  
4. Le Registre est mis à jour à partir de AppEnvConfig. pkgdef et BaseConfig. pkgdef dans le répertoire \Common7\IDE\ShellExtensions\Platform du *chemin d’installation du kit de développement logiciel Visual Studio*. Ces fichiers font partie de Visual Studio et font également partie du package redistribuable Visual Studio Shell (mode isolé).  
  
5. Le Registre est mis à jour à partir du fichier. pkgundef de l’application en supprimant les clés et les entrées spécifiées.  
  
## <a name="run-time-settings"></a>Paramètres d’exécution  
 Lorsqu’un utilisateur démarre l’application Shell isolé, il appelle le point d’entrée de démarrage du shell Visual Studio. Les paramètres d’application sont définis au démarrage de votre application, comme suit :  
  
1. L’interpréteur de commandes de Visual Studio recherche des clés spécifiques dans le registre de l’application. Si le paramètre d’une clé est spécifié dans l’appel au point d’entrée de départ, cette valeur remplace la valeur dans le registre.  
  
2. Si ni le registre ni le paramètre de point d’entrée ne spécifient la valeur d’un paramètre, la valeur par défaut du paramètre est utilisée.  
  
   Quand un utilisateur démarre votre application à partir de la ligne de commande, tous les commutateurs de ligne de commande sont passés au shell Visual Studio, qui les traite de la même façon que devenv. Pour plus d’informations sur les commutateurs devenv, consultez [commutateurs de ligne de commande devenv](../ide/reference/devenv-command-line-switches.md) et [commutateurs de ligne de commande devenv pour le développement VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Pour plus d’informations sur la façon dont un package s’inscrit pour les commutateurs de ligne de commande, consultez [Ajout de commutateurs de ligne de commande](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>Point d’entrée de début  
 Le fichier Appenvstub.dll contient des points d’entrée pour accéder à l’interpréteur de commandes isolé. Lorsque l’application démarre, elle appelle le point d’entrée de début de Appenvstub.dll.  
  
 Vous pouvez modifier le comportement de l’application en modifiant la valeur du dernier paramètre passé au point d’entrée de démarrage. Pour plus d’informations, consultez [paramètres de point d’entrée de Shell isolé (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>La. Fichier vsct  
 Le fichier. vsct vous permet de spécifier les éléments d’interface utilisateur standard de Visual Studio qui sont disponibles dans l’application. Pour plus d’informations, consultez [. Fichiers vsct](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>La. Fichier Pkgundef  
 Lorsque l’application est installée sur un ordinateur sur lequel Visual Studio est déjà installé, une copie des entrées de Registre Visual Studio est créée pour l’application. Par défaut, l’application utilise des VSPackages qui sont déjà installés sur l’ordinateur. Le fichier. pkgundef vous permet d’exclure des entrées de Registre afin de supprimer des éléments spécifiques du shell Visual Studio ou des extensions de l’application. Pour plus d’informations, consultez [. Fichiers Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Le fichier. pkgundef vous permet d’exclure des entrées de Registre afin de supprimer des éléments spécifiques du shell Visual Studio ou des extensions de l’application. Pour plus d’informations, consultez [. Fichiers Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 L’ensemble de GUID de package que vous pouvez exclure est répertorié dans [GUID de package des fonctionnalités Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>La. Fichier pkgdef  
 Le fichier. pkgdef vous permet de définir des entrées de Registre pour l’application qui sont définies lors de l’installation de l’application. Pour obtenir une description du fichier. pkgdef et une liste des entrées de Registre utilisées par le shell Visual Studio, consultez [. Fichiers pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Chaînes de substitution  
 Les chaînes de substitution utilisées dans les fichiers. pkgdef et. pkgundef sont répertoriées dans [chaînes de substitution utilisées dans. Pkgdef et. Fichiers Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Autres paramètres  
 Si votre application d’environnement isolé dépend de Microsoft.VisualStudio.GraphModel.dll, vous devez ajouter la redirection de liaison suivante au fichier. config de votre application de Shell isolé :  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```
