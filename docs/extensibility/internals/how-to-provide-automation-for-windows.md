---
title: 'Comment : Fournir l’automatisation pour Windows ( Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8716fbaa56cdb77063597fd5e07f6e469cc86a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707952"
---
# <a name="how-to-provide-automation-for-windows"></a>Comment : Fournir l’automatisation pour les fenêtres

Vous pouvez fournir l’automatisation pour les fenêtres de documents et d’outils. Fournir l’automatisation est conseillé chaque fois que vous voulez rendre les objets d’automatisation disponibles sur une fenêtre, et l’environnement ne fournit pas déjà un objet d’automatisation prêt à l’emploi, comme il le fait avec une liste de tâches.

## <a name="automation-for-tool-windows"></a>Automatisation pour les fenêtres d’outils

L’environnement fournit l’automatisation sur <xref:EnvDTE.Window> une fenêtre d’outil en retournant un objet standard comme expliqué dans la procédure suivante :

1. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> la méthode via l’environnement avec [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) comme `VSFPROPID` paramètre pour `Window` obtenir l’objet.

2. Lorsqu’un appelant demande un objet d’automatisation spécifique <xref:EnvDTE.Window.Object%2A>à VSPackage pour votre fenêtre d’outil à travers, `QueryInterface` l’environnement `IExtensibleObject`exige, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, ou les `IDispatch` interfaces. Les `IExtensibleObject` `IVsExtensibleObject` deux <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> et de fournir une méthode.

3. Lorsque l’environnement `GetAutomationObject` appelle `NULL`alors la méthode passant, répondez en retournant votre objet spécifique à VSPackage.

4. Si `QueryInterface` `IExtensibleObject` l’appel et `IVsExtensibleObject` échoue, `QueryInterface` `IDispatch`alors l’environnement exige .

## <a name="automation-for-document-windows"></a>Automatisation pour les fenêtres de documents

Un <xref:EnvDTE.Document> objet standard est également disponible à partir de l’environnement, bien `IExtensibleObject` qu’un `GetAutomationObject`éditeur peut avoir sa propre mise en œuvre de l’objet en implémentant l’interface <xref:EnvDTE.Document> et en répondant à .

En outre, un éditeur peut fournir un objet d’automatisation <xref:EnvDTE.Document.Object%2A> spécifique à VSPackage, récupéré par la méthode, en implémentant les `IVsExtensibleObject` interfaces ou `IExtensibleObject` les interfaces. Les [échantillons VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) fournissent un objet d’automatisation spécifique à un document RTF.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
