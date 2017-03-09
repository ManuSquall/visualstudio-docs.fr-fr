---
title: "Informations de l&#39;assembly, bo&#238;te de dialogue | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesAssemblyInfo"
helpviewer_keywords: 
  - "Informations de l’assembly (boîte de dialogue)"
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Informations de l&#39;assembly, bo&#238;te de dialogue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La boîte de dialogue **Informations de l'assembly** sert à spécifier les valeurs des attributs d'assembly globaux [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] qui sont stockés dans le fichier AssemblyInfo créés automatiquement avec votre projet.  Dans l'**Explorateur de solutions**, le fichier se trouve dans le nœud **My Project** dans [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] \(cliquez sur **Afficher tous les fichiers** pour l'afficher\) ; il est localisé sous **Propriétés** dans [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].  Pour plus d'informations sur les attributs d'assembly, consultez [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Pour accéder à cette boîte de dialogue, sélectionnez un nœud de projet dans l'**Explorateur de solutions**, puis cliquez sur **Propriétés** dans le menu **Projet**.  Lorsque le **Concepteur de projets** apparaît, cliquez l'onglet **Application**.  Sur la page **Application**, cliquez sur le bouton **Informations de l'assembly**.  
  
## Liste UIElement  
 **Titre**  
 Spécifie un titre pour le manifeste d'assembly.  Correspond à <xref:System.Reflection.AssemblyTitleAttribute>.  
  
 **Description**  
 Spécifie une description facultative pour le manifeste d'assembly.  Correspond à <xref:System.Reflection.AssemblyDescriptionAttribute>.  
  
 **Société**  
 Spécifie un nom de société pour le manifeste d'assembly.  Correspond à <xref:System.Reflection.AssemblyCompanyAttribute>.  
  
 **Produit**  
 Spécifie un nom de produit pour le manifeste d'assembly.  Correspond à <xref:System.Reflection.AssemblyProductAttribute>.  
  
 **Copyright**  
 Spécifie un texte de copyright pour le manifeste d'assembly.  Correspond à <xref:System.Reflection.AssemblyCopyrightAttribute>.  
  
 **Marque**  
 Spécifie une marque pour le manifeste d'assembly.  Correspond à <xref:System.Reflection.AssemblyTrademarkAttribute>.  
  
 **Version de l'assembly**  
 Spécifie la version de l'assembly.  Correspond à <xref:System.Reflection.AssemblyVersionAttribute>.  
  
 **Version de fichier**  
 Spécifie un numéro de version qui instruit le compilateur d'utiliser une version spécifique pour la ressource de la version du fichier Win32.  Correspond à <xref:System.Reflection.AssemblyFileVersionAttribute>.  
  
 **GUID**  
 GUID unique qui identifie l'assembly.  Lorsque vous créez un projet, Visual Studio génère un GUID pour l'assembly.  Correspond à <xref:System.Guid>.  
  
 **Langage neutre**  
 Spécifie la culture prise en charge par l'assembly.  Correspond à <xref:System.Resources.NeutralResourcesLanguageAttribute>.  La valeur par défaut est **\(Aucune\)**.  
  
 **Rendre l'assembly visible par COM**  
 Spécifie si les types dans l'assembly seront disponibles pour COM.  Correspond à <xref:System.Runtime.InteropServices.ComVisibleAttribute>.  
  
## Voir aussi  
 [Page Application, Concepteur de projets \(Visual Basic\)](../../ide/reference/application-page-project-designer-visual-basic.md)   
 [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)