---
title: "Outils XML dans Visual Studio | Microsoft Docs"
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
  - "vb.xmldesigner"
helpviewer_keywords: 
  - "classes (Visual Studio), XML"
  - "CSS, feuilles de style pour XML"
  - "données (Visual Studio), XML"
  - "groupes de données (Visual Basic), schémas XML"
  - "fichiers de découverte, XML"
  - "modèles pour l'entreprise, XML et"
  - "contrôles serveur, XML et"
  - "SGML, XML"
  - "feuilles de style, pour XML"
  - "contrôles serveur Web, XML"
  - "services Web"
  - "XML (Visual Studio)"
  - "XML (Visual Studio), classes .NET Framework"
  - "XML (Visual Studio), sources de données"
  - "XML (Visual Studio), ressources"
  - "XML (Visual Studio), SGML (relation avec)"
  - "schémas XML"
  - "XMLDataDocument (classe)"
  - "schémas XSD"
  - "XSL"
  - "XSL, feuilles de style"
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Outils XML dans Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le *langage XML \(eXtensible Markup Language\)* est un langage de balisage qui fournit un format pour décrire des données.  Il permet d'effectuer des déclarations de contenu plus précises et d'obtenir des résultats de recherche plus pertinents entre plusieurs plateformes.  De plus, le langage XML permet de séparer la présentation des données.  Par exemple, en HTML, vous utilisez des balises pour indiquer au navigateur d'afficher des données en caractères gras ou italiques, tandis qu'en langage XML, vous utilisez des balises uniquement pour décrire les données, telles qu'un nom de ville, une température ou une pression barométrique.  En XML, vous utilisez des feuilles de style, telles que des feuilles de style en cascade \(CSS\) ou de type XSL \(eXtensible Stylesheet Language\) pour présenter les données dans un navigateur.  Le langage XML sépare les données de la présentation et du processus.  Cela vous permet d'afficher et de traiter les données comme vous le souhaitez, en appliquant différentes feuilles de style et applications.  
  
 Le langage XML est un sous\-ensemble du langage SGML qui est optimisé pour une distribution via Internet.  Il a été défini par le World Wide Web Consortium \(W3C\).  Cette normalisation garantit que les données structurées seront uniformes et indépendantes des applications et des fournisseurs.  
  
 XML est au cœur de nombreuses fonctionnalités de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Les rubriques répertoriées ci\-dessous nomment les outils et les fonctionnalités associés au langage XML qui sont proposés dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Pour plus d'informations, reportez\-vous au [Centre de développement XML](http://go.microsoft.com/fwlink/?LinkID=100176), qui fournit les dernières ressources en matière de documentation, d'informations techniques, de téléchargements et de groupes de discussion, ainsi que d'autres ressources pour les développeurs XML.  
  
## Dans cette section  
 [Utilisation de données XML](../xml-tools/working-with-xml-data.md)  
 Présente le rôle du langage XML dans la manière dont les données sont traitées dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 [Débogage XSLT](../xml-tools/debugging-xslt.md)  
 Fournit des liens vers des rubriques relatives à l'utilisation du débogueur Visual Studio pour déboguer XSLT.  
  
## Référence  
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)  
 Expose l'arborescence d'analyse de l'[éditeur XML](http://go.microsoft.com/fwlink/?LinkId=228249) via [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) pour tout document XML.  
  
 [Référence du standard XML](http://msdn.microsoft.com/fr-fr/79c78508-c9d0-423a-a00f-672e855de401)  
 Fournit des informations sur les technologies XML, y compris le langage XML, la définition de type de document \(DTD\), le langage XSD \(XML Schema Definition\) et XSLT.  
  
 <xref:System.Xml?displayProperty=fullName>  
 Décrit les classes et d'autres éléments qui composent l'espace de noms <xref:System.Xml> et fournit des liens vers des informations plus détaillées sur chaque élément.  
  
 <xref:System.Xml.Serialization?displayProperty=fullName>  
 Décrit les classes et d'autres éléments qui composent l'espace de noms <xref:System.Xml.Serialization> et fournit des liens vers des informations plus détaillées sur chaque élément.  
  
## Rubriques connexes  
 [DOM \(Document Object Model\) XML](../Topic/XML%20Document%20Object%20Model%20\(DOM\).md)  
 Décrit comment la classe <xref:System.Xml.XmlDocument> et les classes qui lui sont associées se conforment aux spécifications de prise en charge d'espace de noms des modèles DOM \(Document Object Model\) \(principaux\) de niveau 1 et de niveau 2 du W3C.  
  
 [Reading XML with the XmlReader](http://msdn.microsoft.com/fr-fr/3029834c-a27e-4331-b7aa-711924062182)  
 Décrit comment la classe <xref:System.Xml.XmlReader> fournit un accès en lecture seule, avant uniquement et non mis en cache aux données XML via un flux XML.  
  
 [Writing XML with the XmlWriter](http://msdn.microsoft.com/fr-fr/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86)  
 Décrit comment la classe <xref:System.Xml.XmlWriter> fournit une manière avant uniquement et sans mise en cache de générer des flux XML, et vous aide à générer des documents XML conformes à la norme W3C.  
  
 [Transformations XSLT](../Topic/XSLT%20Transformations.md)  
 Décrit comment la classe <xref:System.Xml.Xsl.XslCompiledTransform> implémente la recommandation XSLT 1.0.  
  
 [Traitement des données XML à l'aide du modèle de données XPath](../Topic/Process%20XML%20Data%20Using%20the%20XPath%20Data%20Model.md)  
 Décrit comment la classe <xref:System.Xml.XPath.XPathNavigator> peut traiter des données XML stockées dans un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument>.  La classe <xref:System.Xml.XPath.XPathNavigator> est basée sur le modèle de données XQuery 1.0 et XPath 2.0, et peut être utilisée pour parcourir et modifier des données XML.  
  
 [Modèle Objet du schéma \(SOM\) XML](../Topic/XML%20Schema%20Object%20Model%20\(SOM\).md)  
 Décrit les classes utilisées pour créer et manipuler des schémas XML, en fournissant une classe <xref:System.Xml.Schema.XmlSchema> pour charger et modifier un schéma.