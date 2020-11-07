---
title: extraits XML
description: Découvrez la fonctionnalité d’extraits XML dans l’éditeur XML qui vous permet de créer des fichiers XML plus rapidement en réutilisant les extraits XML et en les insérant dans vos fichiers.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9114d50abd8f12e19f67d593927b94afcb010f6
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350190"
---
# <a name="xml-snippets"></a>extraits XML

L’éditeur XML offre une fonctionnalité, appelée *extraits XML* , qui vous permet de créer des fichiers XML plus rapidement. Vous pouvez en effet réutiliser des extraits XML en les insérant dans vos fichiers. Vous pouvez également générer des données XML basées sur un schéma en langage XSD (XML Schema Definition).

## <a name="reusable-xml-snippets"></a>Extraits XML réutilisables

L’éditeur XML comprend de nombreux extraits de code qui couvrent certaines tâches courantes. Il permet ainsi de créer des fichiers XML plus facilement. Par exemple, si vous créez un schéma XML, l’utilisation des extraits de code « élément de séquence de type complexe » et « élément de type simple » insère le texte XML suivant dans votre fichier. Modifiez ensuite la valeur de `name` en fonction de vos besoins.

```xml
<xs:element name="name">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="name">
        <xs:simpleType>
          <xs:restriction base="xs:string"></xs:restriction>
        </xs:simpleType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

Vous pouvez insérer des extraits de deux manières. La commande **Insérer un extrait** insère l’extrait XML à la position du curseur. La commande **entourer de** encapsule l’extrait XML autour du texte sélectionné. Les deux commandes sont disponibles à partir du sous-menu **IntelliSense** du menu **Edition** , ou à partir du menu contextuel dans l’éditeur.

Pour plus d’informations, consultez Guide pratique [pour utiliser des extraits XML](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Extraits XML générés par schéma

L’éditeur XML a également la possibilité de générer un extrait XML à partir d’un schéma XML. Cette fonction permet de remplir un élément avec des éléments XML générés d'après les informations de schéma de cet élément. Pour plus d’informations, consultez [Comment : générer un extrait XML à partir d’un schéma XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Créer des extraits XML

En plus des extraits de code inclus dans Visual Studio par défaut, vous pouvez également créer et utiliser vos propres extraits XML. Pour plus d’informations, consultez [Comment : créer des extraits XML](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Voir aussi

- [Extraits de code dans Visual Studio](../ide/code-snippets.md)
- [Éditeur XML](../xml-tools/xml-editor.md)
