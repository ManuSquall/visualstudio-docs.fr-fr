---
title: 'Comment : fournir une automatisation pour Windows | Microsoft Docs'
description: Découvrez comment fournir une automatisation pour les fenêtres de documents et d’outils dans Visual Studio à l’aide des méthodes Microsoft. VisualStudio. Shell. Interop.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 774b32dc1554fb6d6466be7e915fbaeea8185798
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078745"
---
# <a name="how-to-provide-automation-for-windows"></a>Comment : fournir une automatisation pour Windows

Vous pouvez fournir une automatisation pour les fenêtres de documents et d’outils. L’automatisation est recommandée chaque fois que vous souhaitez rendre des objets Automation disponibles dans une fenêtre, et que l’environnement ne fournit pas déjà un objet Automation prêt à l’emploi, comme c’est le cas avec une liste des tâches.

## <a name="automation-for-tool-windows"></a>Automatisation pour les fenêtres outil

L’environnement fournit l’automatisation sur une fenêtre outil en retournant un <xref:EnvDTE.Window> objet standard comme expliqué dans la procédure suivante :

1. Appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> méthode via l’environnement avec [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) en tant que `VSFPROPID` paramètre pour récupérer l' `Window` objet.

2. Quand un appelant demande un objet Automation spécifique au VSPackage pour votre fenêtre outil par <xref:EnvDTE.Window.Object%2A> le biais de, l’environnement appelle `QueryInterface` pour `IExtensibleObject` , <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> ou les `IDispatch` interfaces. `IExtensibleObject`Et `IVsExtensibleObject` fournissent une <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> méthode.

3. Lorsque l’environnement appelle ensuite la `GetAutomationObject` méthode `NULL` en passant, répond en remettant en retour votre objet spécifique au VSPackage.

4. Si `QueryInterface` l’appel à `IExtensibleObject` et `IVsExtensibleObject` échoue, l’environnement appelle `QueryInterface` pour `IDispatch` .

## <a name="automation-for-document-windows"></a>Automatisation pour les fenêtres de document

Un <xref:EnvDTE.Document> objet standard est également disponible à partir de l’environnement, même si un éditeur peut avoir sa propre implémentation de l' <xref:EnvDTE.Document> objet en implémentant l' `IExtensibleObject` interface et en répondant à `GetAutomationObject` .

En outre, un éditeur peut fournir un objet Automation spécifique au VSPackage, récupéré via la <xref:EnvDTE.Document.Object%2A> méthode, en implémentant `IVsExtensibleObject` les `IExtensibleObject` interfaces ou. Les [exemples VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) contribuent à un objet Automation spécifique aux documents RTF.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
