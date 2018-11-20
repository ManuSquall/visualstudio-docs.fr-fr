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
ms.openlocfilehash: 350908d2d21a30985e624ff9526c22d6e5cf9bb1
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349411"
---
# <a name="xml-tools-in-visual-studio"></a>Outils XML dans Visual Studio

*Langage XML (Extensible Markup)* est un langage de balisage qui fournit un format de description des données. Il permet d'effectuer des déclarations de contenu plus précises et d'obtenir des résultats de recherche plus pertinents entre plusieurs plateformes. De plus, le langage XML permet de séparer la présentation des données. Par exemple, en HTML, vous utilisez des étiquettes pour indiquer au navigateur d’afficher des données en caractères gras ou italiques, tandis qu’en langage XML, vous utilisez des étiquettes uniquement pour décrire les données, telles qu’un nom de ville, une température ou une pression barométrique. Dans XML, vous utilisez des feuilles de style comme feuille de style XSL (Extensible Language) et des feuilles de style en cascade (CSS) pour présenter les données dans un navigateur. Le langage XML sépare les données de la présentation et du processus. Cela vous permet d'afficher et de traiter les données comme vous le souhaitez, en appliquant différentes feuilles de style et applications.

Le langage XML est un sous-ensemble du langage SGML qui est optimisé pour une distribution via Internet. Il a été défini par le World Wide Web Consortium (W3C). Cette normalisation garantit que les données structurées sont uniformes et indépendantes des applications ou des fournisseurs.

XML est au cœur de nombreuses fonctionnalités de Visual Studio et .NET Framework. La liste de l’article suivant nomme les outils et fonctionnalités liées à XML qui sont proposées dans Visual Studio et .NET Framework.

Pour plus d’informations, consultez le <xref:System.Xml?displayProperty=fullName> documentation.

## <a name="reference"></a>Référence

[Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699) expose le [éditeur XML](http://go.microsoft.com/fwlink/?LinkId=228249) arborescence par le biais d’analyse [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) pour tous les documents XML.

[Référence du standard XML](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) fournit des informations sur les technologies XML, notamment XML, définition de Type de Document (DTD), langage de définition de schéma XML (XSD) et XSLT.

<xref:System.Xml?displayProperty=fullName> Décrit les classes et autres éléments qui composent le <xref:System.Xml> espace de noms fournit des liens vers des informations plus détaillées sur chaque élément.

<xref:System.Xml.Serialization?displayProperty=fullName> Décrit les classes et autres éléments qui composent le <xref:System.Xml.Serialization> espace de noms et fournit des liens vers des informations détaillées sur chaque élément.

## <a name="related-sections"></a>Rubriques connexes

[Modèle DOM (Document objet Model) XML](/dotnet/standard/data/xml/xml-document-object-model-dom) décrit comment la <xref:System.Xml.XmlDocument> et ses classes associées conformes aux spécifications de prise en charge des espaces de noms de niveau 2 et W3C Document Object Model (Core), niveau 1.

[Traitement des données XML avec XmlReader et XmlWriter](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc189001\(v\=vs.95\))

[Transformations XSLT](/dotnet/standard/data/xml/xslt-transformations) décrit comment la <xref:System.Xml.Xsl.XslCompiledTransform> classe implémente la recommandation XSLT 1.0.

[Traiter des données XML à l’aide du modèle de données XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model) décrit comment la <xref:System.Xml.XPath.XPathNavigator> classe peut traiter des données XML stockées dans un <xref:System.Xml.XPath.XPathDocument> ou un <xref:System.Xml.XmlDocument> objet. La classe <xref:System.Xml.XPath.XPathNavigator> est basée sur le modèle de données XQuery 1.0 et XPath 2.0, et peut être utilisée pour parcourir et modifier des données XML.

[Modèle SOM (Schema Object Model) XML](/dotnet/standard/data/xml/xml-schema-object-model-som) décrit les classes utilisées pour créer et manipuler des schémas XML, en fournissant un <xref:System.Xml.Schema.XmlSchema> classe pour charger et modifier un schéma.