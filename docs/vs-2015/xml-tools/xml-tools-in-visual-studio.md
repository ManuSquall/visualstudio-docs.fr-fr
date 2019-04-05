---
title: Outils XML
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2812e45460778a3527f55522c6d3fc98285a548d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951691"
---
# <a name="xml-tools-in-visual-studio"></a>Outils XML dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Langage XML (Extensible Markup) * est un langage de balisage qui fournit un format de description des données. Il permet d'effectuer des déclarations de contenu plus précises et d'obtenir des résultats de recherche plus pertinents entre plusieurs plateformes. De plus, le langage XML permet de séparer la présentation des données. Par exemple, en HTML, vous utilisez des balises pour indiquer au navigateur d'afficher des données en caractères gras ou italiques, tandis qu'en langage XML, vous utilisez des balises uniquement pour décrire les données, telles qu'un nom de ville, une température ou une pression barométrique. En XML, vous utilisez des feuilles de style, telles que des feuilles de style en cascade (CSS) ou de type XSL (eXtensible Stylesheet Language) pour présenter les données dans un navigateur. Le langage XML sépare les données de la présentation et du processus. Cela vous permet d'afficher et de traiter les données comme vous le souhaitez, en appliquant différentes feuilles de style et applications.

 Le langage XML est un sous-ensemble du langage SGML qui est optimisé pour une distribution via Internet. Il a été défini par le World Wide Web Consortium (W3C). Cette normalisation garantit que les données structurées seront uniformes et indépendantes des applications et des fournisseurs.

 XML est au cœur de nombreuses fonctionnalités de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Les rubriques répertoriées ci-dessous nomment les outils et les fonctionnalités associés au langage XML qui sont proposés dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

 Pour plus d’informations, consultez le [centre de développement XML](http://go.microsoft.com/fwlink/?LinkID=100176), qui fournit la documentation la plus récente, des informations techniques, des téléchargements, des groupes de discussion et d’autres ressources pour les développeurs XML.

## <a name="in-this-section"></a>Dans cette section
 [Utilisation des données XML](../xml-tools/working-with-xml-data.md) présente le rôle du langage XML dans les façon dont les données est géré dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 [Débogage XSLT](../xml-tools/debugging-xslt.md) fournit des liens vers des rubriques sur l’utilisation du débogueur Visual Studio pour déboguer XSLT.

## <a name="reference"></a>Référence
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699) expose le [éditeur XML](http://go.microsoft.com/fwlink/?LinkId=228249) arborescence par le biais d’analyse [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) pour tous les documents XML.

 [Référence du standard XML](http://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) fournit des informations sur les technologies XML, notamment XML, définition de Type de Document (DTD), langage de définition de schéma XML (XSD) et XSLT.

 <xref:System.Xml?displayProperty=fullName> Décrit les classes et autres éléments qui composent le <xref:System.Xml> espace de noms fournit des liens vers des informations plus détaillées sur chaque élément.

 <xref:System.Xml.Serialization?displayProperty=fullName> Décrit les classes et autres éléments qui composent le <xref:System.Xml.Serialization> espace de noms et fournit des liens vers des informations détaillées sur chaque élément.

## <a name="related-sections"></a>Rubriques connexes
 [Modèle DOM (Document objet Model) XML](http://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) décrit comment la <xref:System.Xml.XmlDocument> et ses classes associées conformes aux spécifications de prise en charge des espaces de noms de niveau 2 et W3C Document Object Model (Core), niveau 1.

 [Lecture de XML avec XmlReader](http://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) décrit comment la <xref:System.Xml.XmlReader> fournit un vers l’avant uniquement, en lecture seule accès aux données XML via un flux XML.

 [Écriture de XML avec XmlWriter](http://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) décrit comment la <xref:System.Xml.XmlWriter> fournit un avant uniquement, de génération de flux de données XML et vous permet de créer des documents XML conformes à la norme W3C.

 [Transformations XSLT](http://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) décrit comment la <xref:System.Xml.Xsl.XslCompiledTransform> classe implémente la recommandation XSLT 1.0.

 [Traiter les données XML à l’aide du modèle de données XPath](http://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) décrit comment la <xref:System.Xml.XPath.XPathNavigator> classe peut traiter des données XML stockées dans un <xref:System.Xml.XPath.XPathDocument> ou un <xref:System.Xml.XmlDocument> objet. La classe <xref:System.Xml.XPath.XPathNavigator> est basée sur le modèle de données XQuery 1.0 et XPath 2.0, et peut être utilisée pour parcourir et modifier des données XML.

 [Modèle SOM (Schema Object Model) XML](http://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) décrit les classes utilisées pour créer et manipuler des schémas XML, en fournissant un <xref:System.Xml.Schema.XmlSchema> classe pour charger et modifier un schéma.
