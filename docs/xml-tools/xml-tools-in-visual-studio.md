---
title: Outils XML dans Visual Studio | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET Framework classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 38d933199c85bee3fa85a533f9c61c08bee898ea
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="xml-tools-in-visual-studio"></a>Outils XML dans Visual Studio

*Langage XML (Extensible Markup)* est un langage de balisage qui fournit un format pour décrire des données. Il permet d'effectuer des déclarations de contenu plus précises et d'obtenir des résultats de recherche plus pertinents entre plusieurs plateformes. De plus, le langage XML permet de séparer la présentation des données. Par exemple, en HTML, vous utilisez des balises pour indiquer au navigateur d'afficher des données en caractères gras ou italiques, tandis qu'en langage XML, vous utilisez des balises uniquement pour décrire les données, telles qu'un nom de ville, une température ou une pression barométrique. En XML, vous utilisez des feuilles de style, telles que des feuilles de style en cascade (CSS) ou de type XSL (eXtensible Stylesheet Language) pour présenter les données dans un navigateur. Le langage XML sépare les données de la présentation et du processus. Cela vous permet d'afficher et de traiter les données comme vous le souhaitez, en appliquant différentes feuilles de style et applications.

Le langage XML est un sous-ensemble du langage SGML qui est optimisé pour une distribution via Internet. Il a été défini par le World Wide Web Consortium (W3C). Cette normalisation garantit que les données structurées seront uniformes et indépendantes des applications et des fournisseurs.

XML est au cœur de nombreuses fonctionnalités de Visual Studio et le .NET Framework. Les rubriques répertoriées ci-dessous désigne les outils et fonctionnalités associées au langage XML qui sont proposées dans Visual Studio et le .NET Framework.

Pour plus d’informations, consultez le <xref:System.Xml?displayProperty=fullName> documentation.

## <a name="in-this-section"></a>Dans cette section

[Utilisation de données XML](../xml-tools/working-with-xml-data.md)  
Décrit le rôle du langage XML dans le traitement des données dans Visual Studio.

[Débogage XSLT](../xml-tools/debugging-xslt.md)  
Fournit des liens vers des rubriques relatives à l'utilisation du débogueur Visual Studio pour déboguer XSLT.

## <a name="reference"></a>Référence

[Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)  
Expose les [éditeur XML](http://go.microsoft.com/fwlink/?LinkId=228249) arborescence par le biais d’analyse [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) pour tous les documents XML.

[Référence du standard XML](http://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401)  
Fournit des informations sur les technologies XML, y compris le langage XML, la définition de type de document (DTD), le langage XSD (XML Schema Definition) et XSLT.

<xref:System.Xml?displayProperty=fullName>  
Décrit les classes et d'autres éléments qui composent l'espace de noms <xref:System.Xml> et fournit des liens vers des informations plus détaillées sur chaque élément.

<xref:System.Xml.Serialization?displayProperty=fullName>  
Décrit les classes et d'autres éléments qui composent l'espace de noms <xref:System.Xml.Serialization> et fournit des liens vers des informations plus détaillées sur chaque élément.

## <a name="related-sections"></a>Rubriques connexes

[DOM (Document Object Model) XML](/dotnet/standard/data/xml/xml-document-object-model-dom)  
Décrit comment la classe <xref:System.Xml.XmlDocument> et les classes qui lui sont associées se conforment aux spécifications de prise en charge d'espace de noms des modèles DOM (Document Object Model) (principaux) de niveau 1 et de niveau 2 du W3C.

[Traitement des données XML avec XmlReader et XmlWriter](https://msdn.microsoft.com/library/cc189001(v=vs.95).aspx)

[Transformations XSLT](/dotnet/standard/data/xml/xslt-transformations)  
Décrit comment la classe <xref:System.Xml.Xsl.XslCompiledTransform> implémente la recommandation XSLT 1.0.

[Traitement des données XML à l’aide du modèle de données XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)  
Décrit comment la classe <xref:System.Xml.XPath.XPathNavigator> peut traiter des données XML stockées dans un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument>. La classe <xref:System.Xml.XPath.XPathNavigator> est basée sur le modèle de données XQuery 1.0 et XPath 2.0, et peut être utilisée pour parcourir et modifier des données XML.

[Modèle Objet du schéma (SOM) XML](/dotnet/standard/data/xml/xml-schema-object-model-som)  
Décrit les classes utilisées pour créer et manipuler des schémas XML, en fournissant une classe <xref:System.Xml.Schema.XmlSchema> pour charger et modifier un schéma.