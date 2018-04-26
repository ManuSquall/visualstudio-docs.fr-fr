---
title: Outils XML dans Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 279a0a73f24b2916e21293c854692ab40f444b4c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="xml-tools-in-visual-studio"></a>Outils XML dans Visual Studio

*Langage XML (Extensible Markup)* est un langage de balisage qui fournit un format pour décrire des données. Il permet d'effectuer des déclarations de contenu plus précises et d'obtenir des résultats de recherche plus pertinents entre plusieurs plateformes. De plus, le langage XML permet de séparer la présentation des données. Par exemple, en HTML, vous utilisez des balises pour indiquer au navigateur d'afficher des données en caractères gras ou italiques, tandis qu'en langage XML, vous utilisez des balises uniquement pour décrire les données, telles qu'un nom de ville, une température ou une pression barométrique. En XML, vous utilisez des feuilles de style, telles que des feuilles de style en cascade (CSS) ou de type XSL (eXtensible Stylesheet Language) pour présenter les données dans un navigateur. Le langage XML sépare les données de la présentation et du processus. Cela vous permet d'afficher et de traiter les données comme vous le souhaitez, en appliquant différentes feuilles de style et applications.

Le langage XML est un sous-ensemble du langage SGML qui est optimisé pour une distribution via Internet. Il a été défini par le World Wide Web Consortium (W3C). Cette normalisation garantit que les données structurées seront uniformes et indépendantes des applications et des fournisseurs.

XML est au cœur de nombreuses fonctionnalités de Visual Studio et le .NET Framework. Les rubriques répertoriées ci-dessous désigne les outils et fonctionnalités associées au langage XML qui sont proposées dans Visual Studio et le .NET Framework.

Pour plus d’informations, consultez le <xref:System.Xml?displayProperty=fullName> documentation.

## <a name="reference"></a>Référence

[Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699) expose le [éditeur XML](http://go.microsoft.com/fwlink/?LinkId=228249) arborescence par le biais d’analyse [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) pour tous les documents XML.

[Référence du standard XML](http://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) fournit des informations sur les technologies XML, notamment XML, définition de Type de Document (DTD), langage de définition de schéma XML (XSD) et XSLT.

<xref:System.Xml?displayProperty=fullName> Décrit les classes et autres éléments qui composent le <xref:System.Xml> espace de noms et fournit des liens vers des informations plus détaillées sur chaque élément.

<xref:System.Xml.Serialization?displayProperty=fullName> Décrit les classes et autres éléments qui composent le <xref:System.Xml.Serialization> espace de noms et fournit des liens vers des informations plus détaillées sur chaque élément.

## <a name="related-sections"></a>Rubriques connexes

[Modèle DOM (Document objet Model) XML](/dotnet/standard/data/xml/xml-document-object-model-dom) décrit comment la <xref:System.Xml.XmlDocument> et ses classes associées conformes aux spécifications de prise en charge des espaces de noms de niveau 2 et W3C Document Object Model (Core), niveau 1.

[Traitement des données XML avec XmlReader et XmlWriter](https://msdn.microsoft.com/library/cc189001(v=vs.95).aspx)

[Transformations XSLT](/dotnet/standard/data/xml/xslt-transformations) décrit comment la <xref:System.Xml.Xsl.XslCompiledTransform> classe implémente la recommandation XSLT 1.0.

[Traitement XML à l’aide de données du modèle de données XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model) décrit comment la <xref:System.Xml.XPath.XPathNavigator> classe peut traiter les données XML stockées dans un <xref:System.Xml.XPath.XPathDocument> ou un <xref:System.Xml.XmlDocument> objet. La classe <xref:System.Xml.XPath.XPathNavigator> est basée sur le modèle de données XQuery 1.0 et XPath 2.0, et peut être utilisée pour parcourir et modifier des données XML.

[Modèle SOM (Schema Object Model) XML](/dotnet/standard/data/xml/xml-schema-object-model-som) décrit les classes utilisées pour créer et manipuler des schémas XML, en fournissant une <xref:System.Xml.Schema.XmlSchema> classe pour charger et modifier un schéma.