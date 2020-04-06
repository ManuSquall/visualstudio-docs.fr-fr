---
title: Enregistrement d’une fenêtre d’outil Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e7971de5ae5301d99147bbfc374dda6b039662a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701603"
---
# <a name="register-a-tool-window"></a>Enregistrer une fenêtre d’outil
Vous pouvez enregistrer vos <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>fenêtres d’outils à l’aide et .

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

 Dans le code <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> ci-dessus, `DynamicWindowPane` les enregistre les fenêtres et les `PersistedWindowPane` fenêtres d’outils avec Visual Studio. La fenêtre d’outil persistée est amarrée et tabbed avec **Solution Explorer**, et la fenêtre dynamique est donnée une position de départ par défaut et la taille. La fenêtre dynamique est rendue transitoire, ce qui indique qu’elle n’est pas créée sur le démarrage. Cela écrit `DontForceCreate` une `ToolWindows` valeur dans la clé dans le registre du système. Pour plus d’informations, voir [la configuration de l’affichage de fenêtre d’outil](/visualstudio/extensibility/tool-window-display-configuration?view=vs-2015).
