---
title: "Procédure : générer un extrait XML à partir d'un schéma XML"
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2c128d2a-aaa6-4814-aa95-e07056afe338
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae55428b61053fbd255446833cb20aec3da79b6e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645382"
---
# <a name="how-to-generate-an-xml-snippet-from-an-xml-schema"></a>Comment : générer un extrait XML à partir d’un schéma XML

L’éditeur XML a la possibilité de générer des extraits XML à partir d’un schéma en langage XSD (XML Schema Definition). Par exemple, lorsque vous créez un fichier XML, alors que vous êtes positionné en regard du nom de l’élément, vous pouvez appuyer sur la touche **Tab** pour remplir l’élément avec les données XML générées à partir des informations de schéma de cet élément.

Cette fonction n'est disponible que pour les éléments. Les règles suivantes s'appliquent également :

- L'élément doit avoir un type de schéma associé ; autrement dit, l'élément doit être valide par rapport à un schéma associé. Le type de schéma ne peut pas être abstract et doit contenir les attributs et/ou éléments enfants obligatoires.

- L'élément actuel dans l'éditeur doit être vide et dépourvu d'attributs. Par exemple, toutes les écritures suivantes sont valides.

  - `<Account`

  - `<Account>`

  - `<Account></Account>`

- Le curseur doit être placé immédiatement à droite du nom de l'élément.

L'extrait généré contient tous les attributs et éléments requis. Si `minOccurs` est supérieur à un, le nombre minimal d'instances requises de cet élément est inclus dans l'extrait, jusqu'à 100 instances. Toutes les valeurs fixes trouvées dans le schéma engendrent des valeurs fixes dans l'extrait. Les éléments `xsd:any` et `xsd:anyAttribute` sont ignorés et n'engendrent aucune construction d'extrait supplémentaire.

Des valeurs par défaut sont générées et notées comme valeurs modifiables. Si le schéma spécifie une valeur par défaut, celle-ci est utilisée. Toutefois, si la valeur par défaut du schéma est une chaîne vide, l'éditeur génère les valeurs par défaut de la manière suivante :

- Si le type de schéma contient des facettes d'énumération, que ce soit directement ou indirectement par le biais de membres d'un type d'union, la première valeur énumérée trouvée dans le modèle Objet du schéma est utilisée comme valeur par défaut.

- Si le type de schéma est un type atomique, l'éditeur cherche ce type atomique et en insère le nom. Pour un type simple dérivé, il utilise le type simple de base. Pour un type de liste, le type atomique est l'`itemType`. Pour une union, le type atomique est celui du premier `memberType`.

## <a name="example"></a>Exemple

Les étapes de cette section vous montrent comment utiliser la fonctionnalité d’extrait XML généré par schéma de l’éditeur XML.

> [!NOTE]
> Avant d'entamer ces procédures, enregistrez le fichier de schéma sur votre ordinateur local.

### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Pour créer un nouveau fichier XML et l’associer à un schéma XML

1. Dans le menu **fichier** , pointez sur **nouveau**, puis cliquez sur **fichier**.

2. Sélectionnez **fichier XML** dans le volet **modèles** , puis cliquez sur **ouvrir**.

     Un nouveau fichier s'ouvre dans l'éditeur. Il contient une déclaration XML par défaut, `<?xml version="1.0" encoding="utf-8">`.

3. Dans la fenêtre Propriétés du document, cliquez sur le bouton Parcourir ( **...** ) du champ **schémas** .

     La boîte de dialogue **schémas XSD** s’affiche.

4. Cliquez sur **Ajouter**.

     La boîte de dialogue **ouvrir le schéma XSD** s’affiche.

5. Sélectionnez le fichier de schéma, puis cliquez sur **ouvrir**.

6. Cliquez sur **OK**.

     Le schéma XML est désormais associé au document XML.

### <a name="to-generate-an-xml-snippet"></a>Pour générer un extrait XML

1. Entrez `<` dans le volet de l'éditeur.

2. La liste des membres affiche les éléments possibles :

     **!--** pour ajouter un commentaire.

     **! DOCTYPE** pour ajouter un type de document.

     **?** permet d'ajouter une instruction de traitement.

     **Contactez** pour ajouter l’élément racine.

3. Sélectionnez **contact** dans la liste des membres et appuyez sur **entrée**.

     L’éditeur ajoute l’étiquette de début `<Contact` et place le curseur après le nom de l’élément.

4. Appuyez sur **Tab** pour générer des données XML pour l’élément `Contact` en fonction de ses informations de schéma.

## <a name="input"></a>Entrée

La procédure pas à pas utilise le fichier de schéma suivant.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<xs:schema elementFormDefault="qualified"
           xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:simpleType name="phoneType">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Voice"/>
      <xs:enumeration value="Fax"/>
      <xs:enumeration value="Pager"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:element name="Contact">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="Name">
          <xs:simpleType>
            <xs:restriction base="xs:string"></xs:restriction>
          </xs:simpleType>
        </xs:element>
        <xs:element name="Title"
                    type="xs:string" />
        <xs:element name="Phone"
                    minOccurs="1"
                    maxOccurs="unbounded">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="Number"
                          minOccurs="1">
                <xs:simpleType>
                  <xs:restriction base="xs:string"></xs:restriction>
                </xs:simpleType>
              </xs:element>
              <xs:element name="Type"
                          default="Voice"
                          minOccurs="1"
                          type="phoneType"/>
            </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

### <a name="output"></a>Sortie

Voici les données XML générées sur la base des informations de schéma associées à l'élément `Contact`. Les éléments marqués comme `bold` désigner les champs modifiables dans l’extrait XML.

```xml
<Contact>
  <Name>name</Name>
  <Title>title</Title>
  <Phone>
    <Number>number</Number>
    <Type>Voice</Type>
  </Phone>
</Contact>
```

## <a name="see-also"></a>Voir aussi

- [Extraits XML](../xml-tools/xml-snippets.md)
- [Comment : utiliser des extraits XML](../xml-tools/how-to-use-xml-snippets.md)
