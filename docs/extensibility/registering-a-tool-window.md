---
title: Inscription d’une fenêtre outil | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34fddd6513aad612398c700b935c6d1d3ee72b59
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186264"
---
# <a name="register-a-tool-window"></a>Inscrire une fenêtre outil
Vous pouvez inscrire vos fenêtres outil à l’aide de <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> et <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>.

## <a name="example"></a>Exemple

```csharp

[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]
[ProvideMenuResource(1000, 1)]
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]
public class PackageToolWindow : Package
{
```

 Dans le code ci-dessus, le <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> inscrit les fenêtres outil `PersistedWindowPane` et `DynamicWindowPane` dans Visual Studio. La fenêtre outil rendue persistante est ancrée et avec des onglets **Explorateur de solutions**, et la fenêtre dynamique reçoit une position et une taille de départ par défaut. La fenêtre dynamique est rendue temporaire, ce qui indique qu’elle n’est pas créée au démarrage. Cela écrit une valeur `DontForceCreate` dans la clé de `ToolWindows` dans le registre système. Pour plus d’informations, consultez Configuration de l’affichage de la [fenêtre outil](/visualstudio/extensibility/tool-window-display-configuration?view=vs-2015).
