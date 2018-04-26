---
title: Extraits XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f92b96f09353bf8e432d6a3931a534064ad7c446
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="xml-snippets"></a>Extraits XML

L’éditeur XML offre une fonctionnalité, appelée *extraits XML*, qui vous permet de créer des fichiers XML plus rapidement. Vous pouvez en effet réutiliser des extraits XML en les insérant dans vos fichiers. Vous pouvez également générer des données XML sur la base d'un schéma de langage XSD (XML Schema definition).

## <a name="reusable-xml-snippets"></a>Extraits XML réutilisables

L'éditeur XML comprend de nombreux extraits couvrant certaines tâches courantes. Il permet ainsi de créer des fichiers XML plus facilement. Par exemple, si vous créez un schéma XML, vous pouvez utiliser les extraits « Élément de séquence de type complexe » et « Élément de type simple » pour insérer le texte XML suivant dans votre fichier. Modifiez ensuite la valeur de `name` en fonction de vos besoins.

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

 Vous pouvez insérer des extraits de deux manières. Le **insérer un extrait** commande insère l’extrait XML à la position du curseur. Le **entourer** commande encapsule l’extrait XML autour du texte sélectionné. Les deux commandes sont disponibles à partir de la **IntelliSense** sous-menu sous le **modifier** menu, ou dans le menu contextuel de l’éditeur.

 Pour plus d’informations, consultez [Comment : utiliser des extraits de code XML](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Extraits XML générés par schéma
 L'éditeur XML permet également de générer un extrait XML à partir d'un schéma XML. Cette fonctionnalité permet de remplir un élément avec des éléments XML générés d’après les informations de schéma de cet élément.

 Pour plus d’informations, consultez [Comment : générer un XML extrait d’un schéma XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Création de nouveaux extraits XML
 Outre les extraits de code sont inclus avec [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio par défaut, vous pouvez également créer et utiliser vos propres extraits XML.

 Pour plus d’informations, consultez [Comment : créer des extraits de code XML](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Voir aussi

- [Éditeur XML](../xml-tools/xml-editor.md)