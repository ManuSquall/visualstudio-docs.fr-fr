---
title: 'Procédure pas à pas : À l’aide des fonctionnalités de l’éditeur XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 27e9d1ce86064c23e3a293382ff7f83389d693f1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60109042"
---
# <a name="walkthrough-using-xml-editor-features"></a>Procédure pas à pas : À l’aide des fonctionnalités de l’éditeur XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les étapes de cette procédure pas à pas expliquent la création d'un document XML. Cette procédure utilise également certaines fonctionnalités de l’éditeur XML qui en font un outil précieux pour l’édition XML.  
  
> [!NOTE]
>  Avant d'entamer cette procédure, enregistrez le fichier hireDate.xsd (plus bas dans cette rubrique) sur votre ordinateur local.  
  
### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Pour créer un nouveau fichier XML et l'associer à un schéma XML  
  
1. Sur le **fichier** menu, pointez sur **New**, puis cliquez sur **fichier**.  
  
2. Sélectionnez **fichier XML** dans le **modèles** volet et cliquez sur **Open**.  
  
     Un nouveau fichier s'ouvre dans l'éditeur. Il contient une déclaration XML par défaut, `<?xml version="1.0" encoding="utf-8">`.  
  
3. Dans la fenêtre de propriétés de document, cliquez sur le bouton Parcourir (**...** ) sur le **schémas** champ.  
  
     Le **schémas XSD** boîte de dialogue s’affiche.  
  
4. Cliquez sur **Ajouter**.  
  
     Le **ouvrir le schéma XSD** boîte de dialogue s’affiche.  
  
5. Sélectionnez le fichier hireDate.xsd et cliquez sur **Open**.  
  
6. Cliquez sur **OK**.  
  
     Le schéma XML est à présent associé au document XML. Ce schéma permet de valider le document. Il est également utilisé par IntelliSense pour remplir la liste de membres d'éléments valides.  
  
### <a name="to-add-data"></a>Pour ajouter des données  
  
1. Entrez `<` dans le volet de l'éditeur.  
  
     La liste des membres affiche les éléments possibles :  
  
    - **!--** pour ajouter un commentaire.  
  
    - **! DOCTYPE** pour ajouter un type de document.  
  
    - **?** permet d'ajouter une instruction de traitement.  
  
    - **employé** pour ajouter l’élément racine.  
  
2. Sélectionnez  **\<!--** pour ajouter un nœud de commentaire et appuyez sur ENTRÉE.  
  
     L'éditeur insère une balise de fin de commentaire et place le curseur entre les balises de début et de fin du commentaire.  
  
3. Tapez dans **fichier Test XML**.  
  
4. Sur une nouvelle ligne, tapez `<`, puis sélectionnez **employé** à partir de la liste des membres.  
  
     L'éditeur ajoute le début d'un élément XML, `<employee`. À ce stade, vous pouvez ajouter des attributs à l'élément ou fermer la balise de fin en entrant `>`.  
  
5. Entrez `>` pour fermer la balise.  
  
6. L'éditeur ajoute la balise de fin. La balise de fin est ajoutée et signalée par un soulignement ondulé indiquant une erreur de validation L’info-bulle affiche le message : L’élément 'employee' contenu est incomplet. 'ID' attendu.  
  
7. Type `<` et sélectionnez **ID** à partir de la liste des membres. Entrez ensuite `>`.  
  
     L'éditeur ajoute l'élément XML `<ID></ID>` et place le curseur après la balise de début ID.  
  
8. Type **abc**.  
  
     Le **abc** texte a une ligne ondulée. L’info-bulle affiche le message : L’élément 'ID' a une valeur non valide selon son type de données.  
  
9. Cliquez avec le bouton droit sur l’élément ID et sélectionnez **atteindre la définition**.  
  
     L'éditeur ouvre le fichier hireDate.xsd dans une nouvelle fenêtre de document et place le curseur sur la définition d'élément de schéma ID.  
  
10. Revenez dans le fichier XML et remplacez le **abc** texte avec **123**.  
  
     La ligne ondulée et l'info-bulle disparaissent sous la valeur de l'élément ID. L’info-bulle de la balise de fin employee affiche maintenant le message : L’élément 'employee' contenu est incomplet. 'hire-date' attendu.  
  
11. Placez le curseur après l’étiquette de fin ID, entrez `<`, sélectionnez hire-date dans la liste des membres, puis entrez `>`.  
  
     L’éditeur ajoute l’élément XML `<hire-date></hire-date>` et place le curseur après l’étiquette de début hire-date.  
  
12. Tapez dans **2003-01-10** pour la valeur de l’élément hire-date.  
  
### <a name="to-format-the-xml-document"></a>Pour mettre en forme le document XML  
  
1. Sélectionnez le **mettre le Document** bouton à partir de la barre d’outils de l’éditeur XML.  
  
     Le document XML est remis en forme.  
  
### <a name="to-save-the-xml-document"></a>Pour enregistrer le document XML  
  
1. À partir de la **fichier** menu, sélectionnez **Enregistrer sous**.  
  
     Le **enregistrer le fichier sous** boîte de dialogue s’affiche. Le nom de fichier par défaut est « XMLFile1 ».  
  
2. Entrez le nom de fichier et l’emplacement du document XML et cliquez sur **enregistrer**.  
  
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
