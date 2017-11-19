---
title: "Comment : générer un extrait XML à partir d’un schéma XML | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c128d2a-aaa6-4814-aa95-e07056afe338
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1090d1509152aaa507220d3119977bb8e9252876
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2017
---
# <a name="how-to-generate-an-xml-snippet-from-an-xml-schema"></a>Procédure : générer un extrait XML à partir d'un schéma XML
L'éditeur XML permet de générer des extraits XML à partir d'un schéma de langage XSD (XML Schema definition). Par exemple, lorsque vous créez un fichier XML alors que le curseur est placé à côté du nom d'un élément, vous pouvez appuyer sur TAB pour remplir l'élément avec des données XML générées à partir des informations de schéma de cet élément.  
  
 Cette fonction n'est disponible que pour les éléments. Les règles suivantes s'appliquent également :  
  
-   L'élément doit avoir un type de schéma associé ; autrement dit, l'élément doit être valide par rapport à un schéma associé. Le type de schéma ne peut pas être abstract et doit contenir les attributs et/ou éléments enfants obligatoires.  
  
-   L'élément actuel dans l'éditeur doit être vide et dépourvu d'attributs. Par exemple, toutes les écritures suivantes sont valides.  
  
    -   `<Account`  
  
    -   `<Account>`  
  
    -   `<Account></Account>`  
  
-   Le curseur doit être placé immédiatement à droite du nom de l'élément.  
  
L'extrait généré contient tous les attributs et éléments requis. Si `minOccurs` est supérieur à un, le nombre minimal d'instances requises de cet élément est inclus dans l'extrait, jusqu'à 100 instances. Toutes les valeurs fixes trouvées dans le schéma engendrent des valeurs fixes dans l'extrait. Les éléments `xsd:any` et `xsd:anyAttribute` sont ignorés et n'engendrent aucune construction d'extrait supplémentaire.  
  
Des valeurs par défaut sont générées et notées comme valeurs modifiables. Si le schéma spécifie une valeur par défaut, celle-ci est utilisée. Toutefois, si la valeur par défaut du schéma est une chaîne vide, l'éditeur génère les valeurs par défaut de la manière suivante :  
  
-   Si le type de schéma contient des facettes d'énumération, que ce soit directement ou indirectement par le biais de membres d'un type d'union, la première valeur énumérée trouvée dans le modèle Objet du schéma est utilisée comme valeur par défaut.  
  
-   Si le type de schéma est un type atomique, l'éditeur cherche ce type atomique et en insère le nom. Pour un type simple dérivé, il utilise le type simple de base. Pour un type de liste, le type atomique est l'`itemType`. Pour une union, le type atomique est celui du premier `memberType`.  
  
## <a name="example"></a>Exemple  
 Les étapes de cette section expliquent l'utilisation de la fonction d'extrait XML généré par schéma dans l'éditeur XML.  
  
> [!NOTE]
>  Avant d'entamer ces procédures, enregistrez le fichier de schéma sur votre ordinateur local.  
  
#### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Pour créer un nouveau fichier XML et l'associer à un schéma XML  
  
1.  Sur le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **fichier**.  
  
2.  Sélectionnez **fichier XML** dans les **modèles** volet et cliquez sur **ouvrir**.  
  
     Un nouveau fichier s'ouvre dans l'éditeur. Il contient une déclaration XML par défaut, `<?xml version="1.0" encoding="utf-8">`.  
  
3.  Dans la fenêtre de propriétés de document, cliquez sur le bouton Parcourir (**...** ) sur le **schémas** champ.  
  
     Le **schémas XSD** boîte de dialogue s’affiche.  
  
4.  Cliquez sur **Ajouter**.  
  
     Le **ouvrir le schéma XSD** boîte de dialogue s’affiche.  
  
5.  Sélectionnez le fichier de schéma et cliquez sur **ouvrir**.  
  
6.  Cliquez sur **OK**.  
  
     Le schéma XML est à présent associé au document XML.  
  
#### <a name="to-generate-an-xml-snippet"></a>Pour générer un extrait XML  
  
1.  Entrez `<` dans le volet de l'éditeur.  
  
2.  La liste des membres affiche les éléments possibles :  
  
     **!--** pour ajouter un commentaire.  
  
     **! DOCTYPE** pour ajouter un type de document.  
  
     **?** permet d'ajouter une instruction de traitement.  
  
     **Contact** pour ajouter l’élément racine.  
  
3.  Sélectionnez **Contact** à partir de la liste des membres et appuyez sur ENTRÉE.  
  
     L'éditeur ajoute la balise de début `<Contact` et place le curseur après le nom de l'élément.  
  
4.  Appuyez sur TAB pour générer des données XML pour l'élément `Contact` d'après ses informations de schéma.  
  
### <a name="input"></a>Entrée  
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
 Voici les données XML générées sur la base des informations de schéma associées à l'élément `Contact`. Les éléments marqués comme `bold` champs modifiables dans l’extrait XML.  
  
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
 [Extraits XML](../xml-tools/xml-snippets.md)   
 [Guide pratique pour utiliser des extraits XML](../xml-tools/how-to-use-xml-snippets.md)