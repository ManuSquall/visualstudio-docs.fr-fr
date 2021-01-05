---
title: Inscription d’une fenêtre outil | Microsoft Docs
description: Découvrez comment vous pouvez inscrire vos fenêtres outil avec Visual Studio à l’aide de aucun ProvideToolWindowAttribute et ProvideToolWindowVisibilityAttribute.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 140375c3c708957343762b72102dcb8920628aba
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863795"
---
# <a name="register-a-tool-window"></a>Inscrire une fenêtre outil
Vous pouvez inscrire vos fenêtres outil à l’aide <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> de et  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> .

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

 Dans le code ci-dessus, le <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> inscrit `PersistedWindowPane` les `DynamicWindowPane` fenêtres outil et dans Visual Studio. La fenêtre outil rendue persistante est ancrée et avec des onglets **Explorateur de solutions**, et la fenêtre dynamique reçoit une position et une taille de départ par défaut. La fenêtre dynamique est rendue temporaire, ce qui indique qu’elle n’est pas créée au démarrage. Cela écrit une `DontForceCreate` valeur dans la `ToolWindows` clé dans le registre système. Pour plus d’informations, consultez Configuration de l’affichage de la [fenêtre outil](/previous-versions/visualstudio/visual-studio-2015/extensibility/tool-window-display-configuration?preserve-view=true&view=vs-2015).