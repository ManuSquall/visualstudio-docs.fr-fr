---
title: 'Comment : fournir une automatisation pour Windows | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f02860b76c80a05808d4e46f315fc3616a19f94f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848852"
---
# <a name="how-to-provide-automation-for-windows"></a>Comment : fournir une automatisation pour Windows

Vous pouvez fournir une automatisation pour les fenêtres de documents et d’outils. L’automatisation est recommandée chaque fois que vous souhaitez rendre des objets Automation disponibles dans une fenêtre, et que l’environnement ne fournit pas déjà un objet Automation prêt à l’emploi, comme c’est le cas avec une liste des tâches.

## <a name="automation-for-tool-windows"></a>Automatisation pour les fenêtres outil

L’environnement fournit l’automatisation sur une fenêtre outil en retournant un objet <xref:EnvDTE.Window> standard comme expliqué dans la procédure suivante :

1. Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> via l’environnement avec [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) en tant que paramètre `VSFPROPID` pour récupérer l’objet `Window`.

2. Quand un appelant demande un objet Automation spécifique au VSPackage pour votre fenêtre outil par le biais de <xref:EnvDTE.Window.Object%2A>, l’environnement appelle `QueryInterface` pour `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>ou les interfaces `IDispatch`. `IExtensibleObject` et `IVsExtensibleObject` fournissent une méthode de <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A>.

3. Lorsque l’environnement appelle ensuite la méthode `GetAutomationObject` qui passe `NULL`, répond en remettant en retour votre objet spécifique au VSPackage.

4. Si l’appel de `QueryInterface` pour `IExtensibleObject` et `IVsExtensibleObject` échoue, l’environnement appelle `QueryInterface` pour `IDispatch`.

## <a name="automation-for-document-windows"></a>Automatisation pour les fenêtres de document

Un objet <xref:EnvDTE.Document> standard est également disponible à partir de l’environnement, même si un éditeur peut avoir sa propre implémentation de l’objet <xref:EnvDTE.Document> en implémentant `IExtensibleObject` interface et en répondant aux `GetAutomationObject`.

En outre, un éditeur peut fournir un objet Automation spécifique au VSPackage, récupéré par le biais de la méthode <xref:EnvDTE.Document.Object%2A>, en implémentant les interfaces `IVsExtensibleObject` ou `IExtensibleObject`. Les [exemples VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) contribuent à un objet Automation spécifique aux documents RTF.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
