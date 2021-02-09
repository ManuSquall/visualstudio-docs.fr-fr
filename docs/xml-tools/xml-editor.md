---
title: Éditeur XML
description: En savoir plus sur l’éditeur XML dans Visual Studio, qui est basé sur l’éditeur de texte et fournit une prise en charge supplémentaire pour les langages XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: de79063eeef5056bd850d8fa1fe76d6698c7e082
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874844"
---
# <a name="xml-editor"></a>Éditeur XML

L’éditeur XML dans Visual Studio est basé sur l’éditeur de texte et comprend une prise en charge supplémentaire des langages XML. Lorsque vous ouvrez un fichier XML dans Visual Studio, il s’ouvre dans l’éditeur XML.

L’éditeur XML comprend les fonctionnalités suivantes :

- Vérification de la syntaxe XML 1.0

- Validation de schéma en cours de frappe

- Prise en charge des extraits XML, notamment des extraits générés par schéma

- Prise en charge des DTD (définition de type de document)

- Prise en charge des schémas de langage XSD (XML Schema definition)

- Création d'un schéma XML à partir d'un document d'instance XML

- Conversion d'une DTD ou d'un schéma XDR (XML-Data Reduced) en un schéma XML

- Vérification de la syntaxe XSLT.

- Mise en plan des documents permettant de développer et réduire les éléments

- Intégration à l' [Explorateur de schémas XML](../xml-tools/xml-schema-explorer.md). Vous disposez ainsi d’une vue hiérarchique des schémas XML.

L’éditeur XML est appelé pour les extensions de fichier connues, telles que *. xml*,. *xsd*, *. xsl* et *. config*. Elle est également appelée sur toute extension de fichier inconnue si le fichier semble contenir du code XML.

## <a name="xslt-intellisense"></a>IntelliSense XSLT

[XSLT IntelliSense](../xml-tools/xml-editor-intellisense-features.md) vous permet d’effectuer une saisie semi-automatique des noms d’ensemble d’attributs, des modes et des noms de modèle, ainsi que des noms de paramètres pour un mode spécifié ou un modèle nommé spécifié.

## <a name="xslt-profiler"></a>Profileur XSLT

Le [profileur XSLT](../xml-tools/xslt-profiler.md) crée des rapports de performances XSLT détaillés qui vous permettent de mesurer, d’évaluer et de cibler les problèmes liés aux performances dans le code XSLT. Le Générateur de profils XSLT inclut également des conseils utiles pour les optimisations de feuille de style XSL et XSLT.

## <a name="xslt-hierarchy"></a>Hiérarchie XSLT

L' [outil hiérarchie XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md) vous permet d’ajouter des points d’arrêt dans les feuilles de style incluses et/ou les règles de modèle intégrées.

## <a name="see-also"></a>Voir aussi

- [Options de l’éditeur XML-mise en forme](../ide/reference/options-text-editor-xml-formatting.md)
- [Options de l’éditeur XML-divers](../ide/reference/options-text-editor-xml-miscellaneous.md)
- [Fonctionnalités de l’éditeur de code](../ide/writing-code-in-the-code-and-text-editor.md)
- [Informations de référence sur les normes XML](/previous-versions/dotnet/netframework-4.0/ms256177(v=vs.100))
- [Outils XML dans Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)