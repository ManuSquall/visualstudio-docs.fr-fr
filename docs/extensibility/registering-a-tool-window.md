---
title: "L’inscription d’une fen&#234;tre outil | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fenêtres Outil, l’inscription gérés"
  - "fenêtres Outil, l’inscription"
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# L’inscription d’une fen&#234;tre outil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez enregistrer vos fenêtres Outil à l’aide de <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> et  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>  
  
## Exemple  
  
```c#  
  
      [ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```  
  
 Dans le code ci\-dessus, la <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> enregistre les fenêtres PersistedWindowPane et DynamicWindowPane avec Visual Studio. La fenêtre outil persistante est ancrée et à onglets avec **l’Explorateur de solutions**, et la fenêtre dynamique position et la taille de début par défaut. La fenêtre dynamique devient temporaire, ce qui signifie qu’il n’est pas créé au démarrage. Écrit une valeur DontForceCreate dans la clé ToolWindows dans le Registre système. Pour plus d'informations, consultez [Configuration de l'affichage fenêtre outil](../extensibility/tool-window-display-configuration.md).