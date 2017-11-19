---
title: "Procédure pas à pas : Utilisation des fonctionnalités de l’éditeur XML | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bf90df0e5311cb1487334ba3851c5083030e2191
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2017
---
# <a name="walkthrough-using-xml-editor-features"></a>Procédure pas à pas : utilisation des fonctionnalités de l’Éditeur XML
Les étapes de cette procédure pas à pas expliquent la création d'un document XML. Cette procédure utilise également certaines fonctions de l'éditeur XML qui en font un outil précieux pour l'édition XML.  
  
> [!NOTE]
>  Avant d'entamer cette procédure, enregistrez le fichier hireDate.xsd (plus bas dans cette rubrique) sur votre ordinateur local.  
  
### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Pour créer un nouveau fichier XML et l'associer à un schéma XML  
  
1.  Sur le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **fichier**.  
  
2.  Sélectionnez **fichier XML** dans les **modèles** volet et cliquez sur **ouvrir**.  
  
     Un nouveau fichier s'ouvre dans l'éditeur. Il contient une déclaration XML par défaut, `<?xml version="1.0" encoding="utf-8">`.  
  
3.  Dans la fenêtre de propriétés de document, cliquez sur le bouton Parcourir (**...** ) sur le **schémas** champ.  
  
     Le **schémas XSD** boîte de dialogue s’affiche.  
  
4.  Cliquez sur **Ajouter**.  
  
     Le **ouvrir le schéma XSD** boîte de dialogue s’affiche.  
  
5.  Sélectionnez le fichier hireDate.xsd et cliquez sur **ouvrir**.  
  
6.  Cliquez sur **OK**.  
  
     Le schéma XML est à présent associé au document XML. Ce schéma permet de valider le document. Il est également utilisé par IntelliSense pour remplir la liste de membres d'éléments valides.  
  
### <a name="to-add-data"></a>Pour ajouter des données  
  
1.  Entrez `<` dans le volet de l'éditeur.  
  
     La liste des membres affiche les éléments possibles :  
  
    -   **!--** pour ajouter un commentaire.  
  
    -   **! DOCTYPE** pour ajouter un type de document.  
  
    -   **?** permet d'ajouter une instruction de traitement.  
  
    -   **employé** pour ajouter l’élément racine.  
  
2.  Sélectionnez **< !--** pour ajouter un nœud de commentaire et appuyez sur ENTRÉE.  
  
     L’éditeur insère une étiquette de fin de commentaire et place le curseur entre les étiquettes de début et de fin du commentaire.  
  
3.  Tapez dans **fichier Test XML**.  
  
4.  Sur une nouvelle ligne, tapez `<`, puis sélectionnez **employé** à partir de la liste des membres.  
  
     L'éditeur ajoute le début d'un élément XML, `<employee`. À ce stade, vous pouvez ajouter des attributs à l'élément ou fermer la balise de fin en entrant `>`.  
  
5.  Entrez `>` pour fermer la balise.  
  
6.  L’éditeur ajoute l’étiquette de fin. La balise de fin est ajoutée et signalée par un soulignement ondulé indiquant une erreur de validation L'info-bulle affiche le message : Le contenu de l'élément 'employee' est incomplet. 'ID' attendu.  
  
7.  Type `<` et sélectionnez **ID** à partir de la liste des membres. Entrez ensuite `>`.  
  
     L'éditeur ajoute l'élément XML `<ID></ID>` et place le curseur après la balise de début ID.  
  
8.  Type **abc**.  
  
     Le **abc** texte a un trait ondulé. L'info-bulle affiche le message : L'élément 'ID' a une valeur non valide selon son type de données.  
  
9. Cliquez avec le bouton droit sur l’élément ID et sélectionnez **atteindre la définition**.  
  
     L'éditeur ouvre le fichier hireDate.xsd dans une nouvelle fenêtre de document et place le curseur sur la définition d'élément de schéma ID.  
  
10. Revenez au fichier XML, puis remplacez le **abc** texte avec **123**.  
  
     La ligne ondulée et l'info-bulle disparaissent sous la valeur de l'élément ID. L'info-bulle de la balise de fin employee affiche à présent le message : Le contenu de l'élément 'employee' est incomplet. 'hire-date' attendu.  
  
11. Placez le curseur après la balise de fin ID, entrez `<`, sélectionnez hire-date dans la liste des membres, puis entrez `>`.  
  
     L'éditeur ajoute l'élément XML `<hire-date></hire-date>` et place le curseur après la balise de début hire-date.  
  
12. Tapez dans **2003-01-10** pour la valeur de la date d’embauche.  
  
### <a name="to-format-the-xml-document"></a>Pour mettre en forme le document XML  
  
- Sélectionnez le **Document au Format** bouton à partir de la barre d’outils de l’éditeur XML.
  
    Le document XML est remis en forme.  
  
### <a name="to-save-the-xml-document"></a>Pour enregistrer le document XML  
  
1.  À partir de la **fichier** menu, sélectionnez **Enregistrer sous**.  
  
     Le **enregistrer le fichier sous** boîte de dialogue s’affiche. Le nom de fichier par défaut est « XMLFile1 ».  
  
2.  Entrez le nom de fichier et l’emplacement du document XML et cliquez sur **enregistrer**.  
  
## <a name="hiredatexsd-file"></a>Fichier hireDate.xsd  
 La procédure pas à pas utilise le fichier de schéma suivant.  
  
```xml
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