---
title: 'Procédure : Fournir l’automatisation pour Windows | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 400b7c89dd10d01fcc7ac4eb238c2bde10117fdd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60086817"
---
# <a name="how-to-provide-automation-for-windows"></a>Procédure : Fournir l’automatisation pour windows

Vous pouvez fournir l’automatisation pour les documents et outils windows. Automatisation de la fourniture est conseillée chaque fois que vous souhaitez rendre disponibles les objets automation sur une fenêtre et l’environnement ne fournit pas déjà un objet automation prêtes à l’emploi, comme il le fait avec une liste de tâches.

## <a name="automation-for-tool-windows"></a>Automation pour les fenêtres Outil

L’environnement fournit l’automation dans une fenêtre outil en retournant une norme <xref:EnvDTE.Window> de l’objet comme expliqué dans la procédure suivante :

1. Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> méthode par le biais de l’environnement avec [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) comme `VSFPROPID` pour obtenir le `Window` objet.

2. Quand un appelant demande un objet d’automation de VSPackage spécifique de votre fenêtre outil via <xref:EnvDTE.Window.Object%2A>, l’environnement appelle `QueryInterface` pour `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, ou le `IDispatch` interfaces. Les deux `IExtensibleObject` et `IVsExtensibleObject` fournissent un <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> (méthode).

3. Lorsque l’environnement appelle ensuite la `GetAutomationObject` méthode en passant `NULL`, répondez en passant sauvegarder votre objet VSPackage spécifique.

4. Si l’appel `QueryInterface` pour `IExtensibleObject` et `IVsExtensibleObject` échoue, l’environnement appelle `QueryInterface` pour `IDispatch`.

## <a name="automation-for-document-windows"></a>Automation pour les fenêtres de document

Une norme <xref:EnvDTE.Document> objet est également disponible à partir de l’environnement, bien qu’un éditeur peut avoir sa propre implémentation de la <xref:EnvDTE.Document> objet en implémentant `IExtensibleObject` interface et la résolution de `GetAutomationObject`.

En outre, un éditeur peut fournir un objet d’automation de VSPackage spécifique, récupéré via la <xref:EnvDTE.Document.Object%2A> méthode, en implémentant le `IVsExtensibleObject` ou `IExtensibleObject` interfaces. Le [exemples d’extensibilité Visual Studio](https://aka.ms/vs2015sdksamples) contribue un objet d’automation spécifiques à un document RTF.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>