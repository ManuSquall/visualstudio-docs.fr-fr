---
title: extraits XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c261893b50a217d888300ca01f3bc190bc065c94
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658757"
---
# <a name="xml-snippets"></a>extraits XML

L’éditeur XML offre une fonctionnalité, appelée *extraits XML*, qui vous permet de créer des fichiers XML plus rapidement. Vous pouvez en effet réutiliser des extraits XML en les insérant dans vos fichiers. Vous pouvez également générer des données XML basées sur un schéma en langage XSD (XML Schema Definition).

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