---
title: "Proc&#233;dure pas &#224; pas&#160;: utilisation des fonctionnalit&#233;s de l&#39;&#201;diteur XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Proc&#233;dure pas &#224; pas&#160;: utilisation des fonctionnalit&#233;s de l&#39;&#201;diteur XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les étapes de cette procédure pas à pas expliquent la création d'un document XML.Cette procédure utilise également certaines fonctions de l'éditeur XML qui en font un outil précieux pour l'édition XML.  
  
> [!NOTE]
>  Avant d'entamer cette procédure, enregistrez le fichier hireDate.xsd \(plus bas dans cette rubrique\) sur votre ordinateur local.  
  
### Pour créer un nouveau fichier XML et l'associer à un schéma XML  
  
1.  Dans le menu **Fichier**, pointez sur **Nouveau** et cliquez sur **Fichier**.  
  
2.  Sélectionnez **Fichier XML** dans le volet **Modèles** et cliquez sur **Ouvrir**.  
  
     Un nouveau fichier s'ouvre dans l'éditeur.Il contient une déclaration XML par défaut, `<?xml version="1.0" encoding="utf-8">`.  
  
3.  Dans la fenêtre de propriétés du document, cliquez sur le bouton Parcourir \(**...**\) du champ **Schémas**.  
  
     La boîte de dialogue **Schémas XSD** s'affiche.  
  
4.  Cliquez sur **Ajouter**.  
  
     La boîte de dialogue **Ouvrir le schéma XSD** s'affiche.  
  
5.  Sélectionnez le fichier hireDate.xsd et cliquez sur **Ouvrir**.  
  
6.  Cliquez sur **OK**.  
  
     Le schéma XML est à présent associé au document XML.Ce schéma permet de valider le document.Il est également utilisé par IntelliSense pour remplir la liste de membres d'éléments valides.  
  
### Pour ajouter des données  
  
1.  Entrez `<` dans le volet de l'éditeur.  
  
     La liste des membres affiche les éléments possibles :  
  
    -   **\!\-\-** permet d'ajouter un commentaire.  
  
    -   **\!DOCTYPE** permet d'ajouter un type de document.  
  
    -   **?** permet d'ajouter une instruction de traitement.  
  
    -   **employee** permet d'ajouter l'élément racine.  
  
2.  Sélectionnez **\<\!\-\-** pour ajouter un nœud de commentaire et appuyez sur ENTRÉE.  
  
     L'éditeur insère une balise de fin de commentaire et place le curseur entre les balises de début et de fin du commentaire.  
  
3.  Entrez Test de fichier XML.  
  
4.  Sur une nouvelle ligne, entrez `<` et sélectionnez **employee** dans la liste des membres.  
  
     L'éditeur ajoute le début d'un élément XML, `<employee`.À ce stade, vous pouvez ajouter des attributs à l'élément ou fermer la balise de fin en entrant `>`.  
  
5.  Entrez `>` pour fermer la balise.  
  
6.  L'éditeur ajoute la balise de fin.La balise de fin est ajoutée et signalée par un soulignement ondulé indiquant une erreur de validationL'info\-bulle affiche le message : Le contenu de l'élément 'employee' est incomplet.'ID' attendu.  
  
7.  Entrez `<` et sélectionnez **ID** dans la liste des membres.Entrez ensuite `>`.  
  
     L'éditeur ajoute l'élément XML `<ID></ID>` et place le curseur après la balise de début ID.  
  
8.  Entrez abc.  
  
     Le texte abc est souligné d'un trait ondulé.L'info\-bulle affiche le message : L'élément 'ID' a une valeur non valide selon son type de données.  
  
9. Cliquez avec le bouton droit sur l'élément ID et sélectionnez **Atteindre la définition**.  
  
     L'éditeur ouvre le fichier hireDate.xsd dans une nouvelle fenêtre de document et place le curseur sur la définition d'élément de schéma ID.  
  
10. Revenez dans le fichier XML et remplacez le texte abc par 123.  
  
     La ligne ondulée et l'info\-bulle disparaissent sous la valeur de l'élément ID.L'info\-bulle de la balise de fin employee affiche à présent le message : Le contenu de l'élément 'employee' est incomplet.'hire\-date' attendu.  
  
11. Placez le curseur après la balise de fin ID, entrez `<`, sélectionnez hire\-date dans la liste des membres, puis entrez `>`.  
  
     L'éditeur ajoute l'élément XML `<hire-date></hire-date>` et place le curseur après la balise de début hire\-date.  
  
12. Entrez 01\-10\-2003 comme valeur de l'élément hire\-date.  
  
### Pour mettre en forme le document XML  
  
1.  Cliquez sur le bouton **Mettre le document en forme** dans la barre d'outils de l'éditeur XML.  
  
     Le document XML est remis en forme.  
  
### Pour enregistrer le document XML  
  
1.  Dans le menu **Fichier**, sélectionnez **Enregistrer sous**.  
  
     La boîte de dialogue **Enregistrer le fichier sous** s'affiche.Le nom de fichier par défaut est « XMLFile1 ».  
  
2.  Entrez le nom de fichier et l'emplacement du document XML, puis cliquez sur **Enregistrer**.  
  
## Fichier hireDate.xsd  
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
  
## Voir aussi  
 [Éditeur XML](../xml-tools/xml-editor.md)