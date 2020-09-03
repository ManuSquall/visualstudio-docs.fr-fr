---
title: 'Comment : fournir une automatisation pour Windows | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7ea7b79df4e7f3748ec2bc7f5e57c6ecb7dfca5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191847"
---
# <a name="how-to-provide-automation-for-windows"></a>Guide pratique pour fournir l’automatisation pour Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous pouvez fournir une automatisation pour les fenêtres de documents et d’outils. L’automatisation est recommandée chaque fois que vous souhaitez rendre des objets Automation disponibles dans une fenêtre, et que l’environnement ne fournit pas déjà un objet Automation prêt à l’emploi, comme c’est le cas avec une liste des tâches.  
  
## <a name="automation-for-tool-windows"></a>Automatisation pour les fenêtres outil  
 L’environnement fournit l’automatisation sur une fenêtre outil en retournant un <xref:EnvDTE.Window> objet standard comme expliqué dans la procédure suivante :  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Pour fournir une automatisation pour les fenêtres outil  
  
1. Appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> méthode via l’environnement en <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> tant que `VSFPROPID` paramètre pour accéder à l' `Window` objet.  
  
2. Quand un appelant demande un objet Automation spécifique au VSPackage pour votre fenêtre outil par <xref:EnvDTE.Window.Object%2A> le biais de, l’environnement appelle `QueryInterface` pour `IExtensibleObject` , <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> ou les `IDispatch` interfaces. `IExtensibleObject`Et `IVsExtensibleObject` fournissent une <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> méthode.  
  
3. Lorsque l’environnement appelle ensuite la `GetAutomationObject` méthode `NULL` en passant, répond en remettant en retour votre objet spécifique au VSPackage.  
  
4. Si `QueryInterface` l’appel à `IExtensibleObject` et `IVsExtensibleObject` échoue, l’environnement appelle `QueryInterface` pour `IDispatch` .  
  
## <a name="automation-for-document-windows"></a>Automatisation pour les fenêtres de document  
 Un <xref:EnvDTE.Document> objet standard est également disponible à partir de l’environnement, même si un éditeur peut avoir sa propre implémentation de l' `T:EnvDTE.Document` objet en implémentant l' `IExtensibleObject` interface et en répondant à `GetAutomationObject` .  
  
 En outre, un éditeur peut fournir un objet Automation spécifique au VSPackage, récupéré via la <xref:EnvDTE.Document.Object%2A> méthode, en implémentant `IVsExtensibleObject` les `IExtensibleObject` interfaces ou. Les [exemples VSSDK](../../misc/vssdk-samples.md) contribuent à un objet Automation spécifique aux documents RTF.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
