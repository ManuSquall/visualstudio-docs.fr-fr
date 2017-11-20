---
title: "Comment : fournir l’automatisation pour Windows | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 945eeb8b81ecb26d43da9528db154d133c4f868c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-provide-automation-for-windows"></a>Comment : fournir l’automatisation pour Windows
Vous pouvez fournir automation pour les documents et outils windows. En fournissant automation est recommandée chaque fois que vous souhaitez rendre disponibles les objets automation dans une fenêtre et l’environnement ne fournit pas déjà un objet automation prêts à l’emploi, comme il le fait avec une liste de tâches.  
  
## <a name="automation-for-tool-windows"></a>Automation pour les fenêtres Outil  
 L’environnement assure l’automatisation dans une fenêtre outil en retournant une norme <xref:EnvDTE.Window> de l’objet comme expliqué dans la procédure suivante :  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Pour fournir l’automatisation pour les fenêtres Outil  
  
1.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> méthode via l’environnement avec <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> en tant que `VSFPROPID` pour obtenir le `Window` objet.  
  
2.  Quand un appelant demande un objet d’automation VSPackage spécifiques de votre fenêtre outil via <xref:EnvDTE.Window.Object%2A>, l’environnement appelle `QueryInterface` pour `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, ou `IDispatch` interfaces. Les deux `IExtensibleObject` et `IVsExtensibleObject` fournissent un <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> (méthode).  
  
3.  Lorsque l’environnement appelle ensuite la `GetAutomationObject` méthode en passant `NULL`, répondre en passant sauvegarder votre objet VSPackage spécifiques.  
  
4.  Si l’appel `QueryInterface` pour `IExtensibleObject` et `IVsExtensibleObject` échoue, l’environnement appelle `QueryInterface` pour `IDispatch`.  
  
## <a name="automation-for-document-windows"></a>Automation pour les fenêtres de Document  
 Une norme <xref:EnvDTE.Document> objet est également disponible à partir de l’environnement, bien qu’un éditeur peut avoir sa propre implémentation de la `T:EnvDTE.Document` objet en implémentant `IExtensibleObject` interface et répond aux requêtes `GetAutomationObject`.  
  
 En outre, un éditeur peut fournir un objet automation VSPackage spécifiques, récupéré via les <xref:EnvDTE.Document.Object%2A> (méthode), en implémentant le `IVsExtensibleObject` ou `IExtensibleObject` interfaces. Le [exemples d’extensibilité Visual Studio](http://aka.ms/vs2015sdksamples) contribue à un objet d’automation spécifiques à un document au format RTF.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>