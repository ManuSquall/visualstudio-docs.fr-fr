---
title: Ajout de commutateurs de ligne de commandement (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f2df3a704c34d97c9d5acfa72249fe492b7f812
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740169"
---
# <a name="add-command-line-switches"></a>Ajouter des commutateurs de ligne de commande
Vous pouvez ajouter des commutateurs de ligne de commande qui s’appliquent à votre VSPackage lorsque *devenv.exe* est exécuté. Utilisez <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> pour déclarer le nom de l’interrupteur et ses propriétés. Dans cet exemple, le commutateur MySwitch est ajouté pour une sous-classe de VSPackage nommée **AddCommandSwitchPackage** sans arguments et avec le VSPackage chargé automatiquement.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 Les paramètres désignés sont indiqués dans les descriptions suivantes.

||||
|-|-|-|-|
| Paramètre | Description|
| Arguments | Le nombre d’arguments pour le commutateur. Peut être "MD", ou une liste d’arguments. |
| Chargement de la demande | Chargez automatiquement le VSPackage si celui-ci est réglé à 1, autrement réglé à 0. |
| HelpString (helpString) | La chaîne d’aide ou d’identification de ressource de la chaîne pour afficher avec **devenv /?**. |
| Nom | L’interrupteur. |
| PackageGuid (packageGuid) | GUID du package. |

 La première valeur des arguments est généralement de 0 ou 1. Une valeur particulière de ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' Cela peut être utile pour débogage des scénarios où un utilisateur doit passer dans une chaîne de commande de débogage.

 La valeur De `true` la charge de `false` demande est soit (1) ou (0) indique que le VSPackage doit être chargé automatiquement.

 La valeur HelpString est l’ID de ressource de la chaîne qui apparaît dans le **devenv /?** Aide à l’affichage. Cette valeur devrait être sous la forme "#nnn" où nnn est un intégrant. La valeur de chaîne dans le fichier de ressources doit se terminer dans un nouveau caractère de ligne.

 La valeur nom est le nom de l’interrupteur.

 La valeur PackageGuid est le GUID du paquet qui implémente ce commutateur. L’IDE utilise ce GUID pour trouver le VSPackage dans le registre auquel le commutateur de ligne de commande s’applique.

## <a name="retrieve-command-line-switches"></a>Récupérer les commutateurs de ligne de commande
 Lorsque votre colis est chargé, vous pouvez récupérer les commutateurs de ligne de commande en remplissant les étapes suivantes.

1. Dans la mise en <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> œuvre <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> votre VSPackage, faites appel `QueryService` pour obtenir l’interface.

2. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> pour récupérer les commutateurs de ligne de commande que l’utilisateur a entrés.

   Le code suivant montre comment savoir si le commutateur de ligne de commande MySwitch a été saisi par l’utilisateur :

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 Il est de votre responsabilité de vérifier les commutateurs de votre ligne de commande chaque fois que votre colis est chargé.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Commutateurs de ligne de commande Devenv](../ide/reference/devenv-command-line-switches.md)
- [Utilitaire CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)
- [. Fichiers Pkgdef](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)
