---
title: "Objet de VSTextBuffer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSTextBuffer"
helpviewer_keywords: 
  - "Objet VSTextBuffer, référence"
  - "vues (Visual Studio SDK), les objets VSTextBuffer"
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Objet de VSTextBuffer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'objet de mémoire tampon de texte représente un flux de texte Unicode, qui est généralement associé à un fichier. Un <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet peut être utilisé en dehors du contexte de l'éditeur de base, comme dans le cas d'un Assistant.  
  
 Le tableau suivant indique les interfaces de `VSTextBuffer`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)|Interface OLE standard. Principalement utilisé pour la gestion des exceptions dans la mémoire tampon Annuler\/Rétablir.|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Interface OLE standard.|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|Interface OLE standard.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permet la création d'actions composés \(autrement dit, les actions qui sont regroupées en une unité d'annulation\/de rétablissement unique\).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Active la persistance des données du document gérées par la mémoire tampon de texte.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fournit des services de base ; utilisé par de nombreux clients.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Permet de rechercher une mémoire tampon.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fournit des lecture et en écriture à l'aide de coordonnées à deux dimensions. Hérite de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fournit des lire et écrire des fonctionnalités à l'aide des coordonnées unidimensionnelles. Hérite de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Offre un accès séquentiel, en fonction du flux de texte dans la mémoire tampon rapide.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fournit l'accès à une collection générique de propriétés. La propriété la plus importante est le nom ou le nom, de la mémoire tampon. Vous pouvez stocker vos propres données aléatoires dans la mémoire tampon avec cette interface par la création d'un GUID et son utilisation en tant que clé.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Prend en charge les points de connexion pour les événements.|  
  
## Notes  
 Le `VSTextBuffer` se trouve généralement par un `QueryInterface` appeler sur `IVsTextBuffer`. Pour plus d'informations, consultez [tampon de texte](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Figures Edit](http://msdn.microsoft.com/fr-fr/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)