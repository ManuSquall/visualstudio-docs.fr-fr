---
title: Ajout de Services Web pour les systèmes de projet | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project systems, adding Web services
- Web services, adding to VSPackage project systems
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
manager: douge
ms.openlocfilehash: 80de75b1b10a761e88b86c0982c0dc925c6eeeb4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501646"
---
# <a name="adding-web-services-to-project-systems"></a>Ajout de services web à des systèmes de projet
En règle générale, les services Web XML sont des ressources adressables par URL qui retournent des informations par programmation au système de projet en utilisant le protocole SOAP (Simple Object Access Protocol). Vous pouvez intégrer des services Web à votre système de projet VSPackage à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> interface.  
  
### <a name="to-add-a-web-service-to-your-project-system"></a>Pour ajouter un service Web à votre système de projet  
  
1.  Appelez `QueryService` pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> par le biais de l’interface <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> service.  
  
2.  Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A>. Si vous passez dans `pDiscoverySession` paramètre en tant que `NULL`, une session de découverte est créée pour vous, et la session est mis en cache afin qu’il soit disponible pour une utilisation ultérieure par le <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> interface. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> méthode retourne un pointeur vers <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2>.  
  
3.  Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A>. Passez l’objet automation pour le dossier de références de service Web en tant que le `pUnkWebReferenceFolder` paramètre. L’environnement Visual Studio vérifie ensuite si le service Web est déjà installé. Si le service Web n’est pas présent, l’environnement télécharge et ajoute le service Web à un dossier et tous les fichiers supplémentaires (tels que les fichiers .wsdl) pour les nœuds enfants du dossier.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>