---
title: "Interception des commandes de Service de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "commandes, l’interception de service de langage"
  - "services de langage, l’interception de commandes"
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Interception des commandes de Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous pouvez avoir des commandes d'interception de service de langage que l'affichage de texte ' sinon.  Cela est utile pour le comportement spécifique au langage que l'affichage de texte ne gère pas.  Vous pouvez désactiver ces commandes en ajoutant un ou plusieurs filtres de commande à l'affichage de texte de votre service de langage.  
  
## Obtention et le routage la commande  
 un filtre de commande est un objet d' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> qui surveille certaines séquences de caractères ou commandes principales.  Vous pouvez associer plusieurs filtre de commande avec un affichage de texte.  Chaque affichage de texte contient des filtres d'une hiérarchie de commandes.  Après avoir créé un nouveau filtre de commande, vous ajoutez le filtre de la chaîne pour l'affichage de texte approprié.  
  
 Appelez la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> sur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pour ajouter votre filtre de commande dans la chaîne.  Lorsque vous appelez l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] retourne un autre filtre de commande dans laquelle vous pouvez passer des commandes que votre filtre de commande ne gère pas.  
  
 Vous disposez des options suivantes pour la gestion de commande :  
  
-   Exécutez la commande puis transmettez la commande au filtre suivant de commande dans la chaîne.  
  
-   Exécutez la commande et ne transmettez pas la commande au filtre suivant de commande.  
  
-   ne gérez pas la commande, mais transmettez la commande au filtre suivant de commande.  
  
-   ignorez la commande.  Le ne gérez pas dans le filtre actif, et ne le passez pas dans le filtre suivant.  
  
 Pour plus d'informations sur les commandes votre service de langage doit gérer, consultez [Commandes importantes pour les filtres de Service de langage](../../extensibility/internals/important-commands-for-language-service-filters.md).