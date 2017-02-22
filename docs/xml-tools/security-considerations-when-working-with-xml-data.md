---
title: "Consid&#233;rations de s&#233;curit&#233; lors de l&#39;utilisation de donn&#233;es XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Consid&#233;rations de s&#233;curit&#233; lors de l&#39;utilisation de donn&#233;es XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique présente les problèmes de sécurité à prendre en compte lors de l'utilisation de l'éditeur XML ou du débogueur XSLT.  
  
## Éditeur XML  
 L'éditeur XML est basé sur l'éditeur de texte Visual Studio.Il repose sur les classes <xref:System.Xml> et <xref:System.Xml.Xsl> pour traiter la plupart des processus XML.  
  
-   Les transformations XSLT s'exécutent dans un nouveau domaine d'application.Les transformations XSLT sont traitées en *sandbox* ; autrement dit, la stratégie de sécurité d'accès au code de votre ordinateur permet de déterminer les autorisations limitées selon l'emplacement de la feuille de style XSLT.Par exemple, les feuilles de style provenant d'un emplacement Internet ont les autorisations les plus limitées, tandis que les feuilles de style copiées vers votre disque dur s'exécutent en Confiance totale.  
  
-   La classe <xref:System.Xml.Xsl.XslCompiledTransform> permet de compiler le XSLT en un langage intermédiaire Microsoft afin d'accélérer l'exécution.  
  
-   Les schémas qui pointent vers un emplacement externe dans le fichier catalogue sont automatiquement téléchargés lors du chargement initial de l'éditeur XML.La classe <xref:System.Xml.Schema.XmlSchemaSet> permet de compiler les schémas.Le fichier catalogue fourni avec l'éditeur XML n'offre aucun lien vers des schémas externes.L'utilisateur doit ajouter explicitement une référence au schéma externe avant que l'éditeur XML télécharge le fichier de schéma.Le téléchargement HTTP peut être désactivé via la page **Divers \(Outils\\Options\)** de l'éditeur XML.  
  
-   L'éditeur XML utilise les classes <xref:System.Net> pour télécharger les schémas  
  
## Débogueur XSLT  
 Le débogueur XSLT utilise le moteur de débogage managé Visual Studio et les classes des espaces de noms <xref:System.Xml> et <xref:System.Xml.Xsl>.  
  
-   Le débogueur XSLT exécute chaque transformation XSLT dans un domaine d'application en sandbox.La stratégie de sécurité d'accès au code de votre ordinateur permet de déterminer les autorisations limitées selon l'emplacement de la feuille de style XSLT.Par exemple, les feuilles de style provenant d'un emplacement Internet ont les autorisations les plus limitées, tandis que les feuilles de style copiées vers votre disque dur s'exécutent en Confiance totale.  
  
-   La feuille de style XSLT est compilée à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
-   L'évaluateur d'expression XSLT est chargé par le moteur de débogage managé.Ce dernier présume que tout le code est exécuté depuis l'ordinateur local de l'utilisateur.De même, la classe <xref:System.Xml.Xsl.XslCompiledTransform> télécharge le fichier XSLT sur l'ordinateur local de l'utilisateur.La possibilité d'élévation du privilège d'exécution est atténuée par le fait que toutes les transformations XSLT sont exécutées dans un nouveau domaine d'application dont les autorisations sont limitées.  
  
## Voir aussi  
 [Application Domains](http://msdn.microsoft.com/fr-fr/39e57d07-a740-4cd4-ae82-e119ea3856c1)