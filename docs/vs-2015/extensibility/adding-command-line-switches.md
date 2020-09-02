---
title: Ajout de commutateurs de ligne de commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e28a3f303849458a407b212d3aad1a8c198f6d25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562274"
---
# <a name="adding-command-line-switches"></a>Ajout de commutateurs de ligne de commande
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez ajouter des commutateurs de ligne de commande qui s’appliquent à votre VSPackage lors de l’exécution de devenv.exe. Utilisez <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> pour déclarer le nom du commutateur et ses propriétés. Dans cet exemple, le commutateur MySwitch est ajouté pour une sous-classe de VSPackage nommée **AddCommandSwitchPackage** sans arguments et avec le VSPackage chargé automatiquement.  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 Les paramètres nommés sont présentés dans le tableau suivant.  
  
 Arguments  
 Nombre d’arguments pour le commutateur. Peut être « * » ou une liste d’arguments.  
  
 DemandLoad  
 Charger le VSPackage automatiquement si cette valeur est définie sur 1, sinon, sur 0.  
  
 HelpString  
 Chaîne d’aide ou ID de ressource de la chaîne à afficher avec **devenv/ ?**.  
  
 Nom  
 Commutateur.  
  
 PackageGuid  
 GUID du package.  
  
 La première valeur des arguments est généralement 0 ou 1. Une valeur spéciale de' * 'peut être utilisée pour indiquer que tout le reste de la ligne de commande est l’argument. Cela peut être utile pour déboguer des scénarios où un utilisateur doit passer une chaîne de commande du débogueur.  
  
 La valeur DemandLoad est `true` (1) ou `false` (0) indique que le VSPackage doit être chargé automatiquement.  
  
 La valeur HelpString est l’ID de ressource de la chaîne qui apparaît dans le devenv/ ? Affichage de l’aide. Cette valeur doit être au format « #nnn », où NNN est un entier. La valeur de chaîne dans le fichier de ressources doit se terminer par un caractère de nouvelle ligne.  
  
 La valeur Name est le nom du commutateur.  
  
 La valeur PackageGuid est le GUID du package qui implémente ce commutateur. L’IDE utilise ce GUID pour rechercher le VSPackage dans le registre auquel le commutateur de ligne de commande s’applique.  
  
## <a name="retrieving-command-line-switches"></a>Récupération des commutateurs de ligne de commande  
 Lorsque votre package est chargé, vous pouvez récupérer les commutateurs de ligne de commande en effectuant les étapes suivantes.  
  
1. Dans l’implémentation de votre VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> , appelez `QueryService` sur <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> pour accéder à l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> interface.  
  
2. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> pour récupérer les commutateurs de ligne de commande entrés par l’utilisateur.  
  
   Le code suivant montre comment déterminer si le commutateur de ligne de commande MySwitch a été entré par l’utilisateur :  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 Il vous incombe de vérifier vos commutateurs de ligne de commande chaque fois que votre package est chargé.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Commutateurs de ligne de commande devenv](../ide/reference/devenv-command-line-switches.md)   
 [Utilitaire CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)   
 [Fichiers .Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
