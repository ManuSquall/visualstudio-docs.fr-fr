---
title: 'Procédure pas à pas : utilisation des fonctionnalités de l’éditeur XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa954cfb356593a4f22a44faddd69acdcfc93e37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669564"
---
# <a name="walkthrough-using-xml-editor-features"></a>Procédure pas à pas : utilisation des fonctionnalités de l'Éditeur XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les étapes de cette procédure pas à pas expliquent la création d'un document XML. Cette procédure utilise également certaines fonctionnalités de l’éditeur XML qui en font un outil précieux pour l’édition XML.

> [!NOTE]
> Avant d'entamer cette procédure, enregistrez le fichier hireDate.xsd (plus bas dans cette rubrique) sur votre ordinateur local.

### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Pour créer un nouveau fichier XML et l'associer à un schéma XML

1. Dans le menu **fichier** , pointez sur **nouveau**, puis cliquez sur **fichier**.

2. Sélectionnez **fichier XML** dans le volet **modèles** , puis cliquez sur **ouvrir**.

     Un nouveau fichier s'ouvre dans l'éditeur. Il contient une déclaration XML par défaut, `<?xml version="1.0" encoding="utf-8">`.

3. Dans la fenêtre Propriétés du document, cliquez sur le bouton Parcourir (**...**) du champ **schémas** .

     La boîte de dialogue **schémas XSD** s’affiche.

4. Cliquez sur **Add**.

     La boîte de dialogue **ouvrir le schéma XSD** s’affiche.

5. Sélectionnez le fichier HireDate. xsd, puis cliquez sur **ouvrir**.

6. Cliquez sur **OK**.

     Le schéma XML est à présent associé au document XML. Ce schéma permet de valider le document. Il est également utilisé par IntelliSense pour remplir la liste de membres d'éléments valides.

### <a name="to-add-data"></a>Pour ajouter des données

1. Entrez `<` dans le volet de l'éditeur.

     La liste des membres affiche les éléments possibles :

    - **!--** pour ajouter un commentaire.

    - **! DOCTYPE** pour ajouter un type de document.

    - **?** permet d'ajouter une instruction de traitement.

    - **employé** pour ajouter l’élément racine.

2. Sélectionnez ** \< !--** pour ajouter un nœud de commentaire et appuyez sur entrée.

     L'éditeur insère une balise de fin de commentaire et place le curseur entre les balises de début et de fin du commentaire.

3. Tapez dans **test XML file**.

4. Sur une nouvelle ligne, tapez `<` , puis sélectionnez **Employee** dans la liste des membres.

     L'éditeur ajoute le début d'un élément XML, `<employee`. À ce stade, vous pouvez ajouter des attributs à l'élément ou fermer la balise de fin en entrant `>`.

5. Entrez `>` pour fermer la balise.

6. L'éditeur ajoute la balise de fin. La balise de fin est ajoutée et signalée par un soulignement ondulé indiquant une erreur de validation L'info-bulle affiche le message : Le contenu de l'élément 'employee' est incomplet. 'ID' attendu.

7. Tapez `<` et sélectionnez **ID** dans la liste des membres. Entrez ensuite `>`.

     L'éditeur ajoute l'élément XML `<ID></ID>` et place le curseur après la balise de début ID.

8. Tapez **ABC**.

     Le texte **ABC** est souligné d’un trait ondulé. L'info-bulle affiche le message : L'élément 'ID' a une valeur non valide selon son type de données.

9. Cliquez avec le bouton droit sur l’élément ID et sélectionnez **atteindre la définition**.

     L'éditeur ouvre le fichier hireDate.xsd dans une nouvelle fenêtre de document et place le curseur sur la définition d'élément de schéma ID.

10. Revenez au fichier XML et remplacez le texte **ABC** par **123**.

     La ligne ondulée et l'info-bulle disparaissent sous la valeur de l'élément ID. L’info-bulle de l’étiquette de fin employee affiche à présent le message : Le contenu de l’élément ’employee’ est incomplet. 'hire-date' attendu.

11. Placez le curseur après l’étiquette de fin ID, entrez `<`, sélectionnez hire-date dans la liste des membres, puis entrez `>`.

     L’éditeur ajoute l’élément XML `<hire-date></hire-date>` et place le curseur après l’étiquette de début hire-date.

12. Tapez **2003-01-10** pour la valeur Hire-date.

### <a name="to-format-the-xml-document"></a>Pour mettre en forme le document XML

1. Sélectionnez le bouton **mettre le document en forme** dans la barre d’outils de l’éditeur XML.

     Le document XML est remis en forme.

### <a name="to-save-the-xml-document"></a>Pour enregistrer le document XML

1. Dans le menu **Fichier**, sélectionnez **Enregistrer sous**.

     La boîte de dialogue **enregistrer le fichier sous** s’affiche. Le nom de fichier par défaut est « XMLFile1 ».

2. Entrez le nom de fichier et l’emplacement du document XML, puis cliquez sur **Enregistrer**.

## <a name="hiredatexsd-file"></a>Fichier hireDate.xsd
 La procédure pas à pas utilise le fichier de schéma suivant.

```
<?xml version="1.0"?>
<xs:schema attributeFormDefault="unqualified"
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"
     xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="employee">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="ID" type="xs:unsignedShort" />
        <xs:element name="hire-date" type="xs:date" />
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

## <a name="see-also"></a>Voir aussi
 [Éditeur XML](../xml-tools/xml-editor.md)
