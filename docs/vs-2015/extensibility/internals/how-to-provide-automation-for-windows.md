---
title: 'Procédure : Fournir l’automatisation pour Windows | Microsoft Docs'
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
ms.openlocfilehash: 38e15c19ad5f9b0596240f473e078ebb6452c22b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949723"
---
# <a name="how-to-provide-automation-for-windows"></a>Procédure : Fournir l’automatisation pour Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous pouvez fournir l’automatisation pour les documents et outils windows. Automatisation de la fourniture est conseillée chaque fois que vous souhaitez rendre disponibles les objets automation sur une fenêtre et l’environnement ne fournit pas déjà un objet automation prêtes à l’emploi, comme il le fait avec une liste de tâches.  
  
## <a name="automation-for-tool-windows"></a>Automatisation de l’outil Windows  
 L’environnement fournit l’automation dans une fenêtre outil en retournant une norme <xref:EnvDTE.Window> de l’objet comme expliqué dans la procédure suivante :  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Pour fournir l’automatisation pour les fenêtres Outil  
  
1.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> méthode par le biais de l’environnement avec <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> comme `VSFPROPID` pour obtenir le `Window` objet.  
  
2.  Quand un appelant demande un objet d’automation de VSPackage spécifique de votre fenêtre outil via <xref:EnvDTE.Window.Object%2A>, l’environnement appelle `QueryInterface` pour `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, ou le `IDispatch` interfaces. Les deux `IExtensibleObject` et `IVsExtensibleObject` fournissent un <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> (méthode).  
  
3.  Lorsque l’environnement appelle ensuite la `GetAutomationObject` méthode en passant `NULL`, répondez en passant sauvegarder votre objet VSPackage spécifique.  
  
4.  Si l’appel `QueryInterface` pour `IExtensibleObject` et `IVsExtensibleObject` échoue, l’environnement appelle `QueryInterface` pour `IDispatch`.  
  
## <a name="automation-for-document-windows"></a>Automatisation de Document Windows  
 Une norme <xref:EnvDTE.Document> objet est également disponible à partir de l’environnement, bien qu’un éditeur peut avoir sa propre implémentation de la `T:EnvDTE.Document` objet en implémentant `IExtensibleObject` interface et la résolution de `GetAutomationObject`.  
  
 En outre, un éditeur peut fournir un objet d’automation de VSPackage spécifique, récupéré via la <xref:EnvDTE.Document.Object%2A> méthode, en implémentant le `IVsExtensibleObject` ou `IExtensibleObject` interfaces. Le [exemples d’extensibilité Visual Studio](../../misc/vssdk-samples.md) contribue un objet d’automation spécifiques à un document RTF.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
