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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9a46523c4c856367e77c345c7e44d0dbc87508f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845983"
---
# <a name="xml-tools-in-visual-studio"></a>Outils XML dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Extensible Markup Language (XML) * est un langage de balisage qui fournit un format pour la description des données. Il permet d'effectuer des déclarations de contenu plus précises et d'obtenir des résultats de recherche plus pertinents entre plusieurs plateformes. De plus, le langage XML permet de séparer la présentation des données. Par exemple, en HTML, vous utilisez des balises pour indiquer au navigateur d'afficher des données en caractères gras ou italiques, tandis qu'en langage XML, vous utilisez des balises uniquement pour décrire les données, telles qu'un nom de ville, une température ou une pression barométrique. En XML, vous utilisez des feuilles de style, telles que des feuilles de style en cascade (CSS) ou de type XSL (eXtensible Stylesheet Language) pour présenter les données dans un navigateur. Le langage XML sépare les données de la présentation et du processus. Cela vous permet d'afficher et de traiter les données comme vous le souhaitez, en appliquant différentes feuilles de style et applications.

 Le langage XML est un sous-ensemble du langage SGML qui est optimisé pour une distribution via Internet. Il a été défini par le World Wide Web Consortium (W3C). Cette normalisation garantit que les données structurées seront uniformes et indépendantes des applications et des fournisseurs.

 XML est au cœur de nombreuses fonctionnalités de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Les rubriques répertoriées ci-dessous nomment les outils et les fonctionnalités associés au langage XML qui sont proposés dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

 Pour plus d’informations, consultez le [Centre de développement XML](https://msdn.microsoft.com/data/bb190600.aspx), qui fournit la documentation la plus récente, des informations techniques, des téléchargements, des groupes de discussion et d’autres ressources pour les développeurs XML.

## <a name="in-this-section"></a>Dans cette section
 [Utilisation de données XML](../xml-tools/working-with-xml-data.md) Décrit le rôle du code XML dans la façon dont les données sont gérées dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 [Débogage XSLT](../xml-tools/debugging-xslt.md) Fournit des liens vers des rubriques sur l’utilisation du débogueur Visual Studio pour déboguer XSLT.

## <a name="reference"></a>Informations de référence
 [ Éditeur deMicrosoft.VisualStudio.Xml](https://msdn.microsoft.com/library/microsoft.visualstudio.xmleditor.aspx) Expose l’arborescence d’analyse de l' [éditeur XML](https://msdn.microsoft.com/library/ms255810.aspx) via [System.Xml. LINQ](https://msdn.microsoft.com/library/system.xml.linq.aspx) pour tous les documents XML.

 Informations de référence sur les [normes XML](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) Fournit des informations sur les technologies XML, notamment XML, la définition de type de document (DTD), le langage XSD (XML Schema Definition) et XSLT.

 <xref:System.Xml?displayProperty=fullName> Décrit les classes et d’autres éléments qui composent l' <xref:System.Xml> espace de noms et fournit des liens vers des informations plus détaillées sur chaque élément.

 <xref:System.Xml.Serialization?displayProperty=fullName> Décrit les classes et d’autres éléments qui composent l' <xref:System.Xml.Serialization> espace de noms et fournit des liens vers des informations plus détaillées sur chaque élément.

## <a name="related-sections"></a>Sections connexes
 [XML Document Object Model (DOM)](https://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) Décrit comment le <xref:System.Xml.XmlDocument> et ses classes associées sont conformes aux spécifications de prise en charge des espaces de noms W3C Document Object Model (Core) Level 1 et Level 2.

 [Lecture de XML avec XmlReader](https://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) Décrit comment le <xref:System.Xml.XmlReader> fournit un accès en lecture seule, avant uniquement et non mis en cache aux données XML via un flux XML.

 [Écriture de XML avec XmlWriter](https://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) Décrit comment le <xref:System.Xml.XmlWriter> fournit un moyen de générer des flux XML non mis en cache uniquement, et vous aide à créer des documents XML conformes à la norme W3C.

 [Transformations XSLT](https://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) Décrit comment la <xref:System.Xml.Xsl.XslCompiledTransform> classe implémente la recommandation XSLT 1,0.

 [Traiter des données XML à l’aide du modèle de données XPath](https://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) Décrit comment la <xref:System.Xml.XPath.XPathNavigator> classe peut traiter des données XML stockées dans un <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> objet ou. La classe <xref:System.Xml.XPath.XPathNavigator> est basée sur le modèle de données XQuery 1.0 et XPath 2.0, et peut être utilisée pour parcourir et modifier des données XML.

 [Modèle d’objet de schéma XML (SOM)](https://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) Décrit les classes utilisées pour créer et manipuler des schémas XML, en fournissant une <xref:System.Xml.Schema.XmlSchema> classe pour charger et modifier un schéma.
