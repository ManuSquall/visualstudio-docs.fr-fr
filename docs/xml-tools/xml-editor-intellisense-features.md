---
title: "Fonctionnalit&#233;s IntelliSense de l&#39;&#201;diteur XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Fonctionnalit&#233;s IntelliSense de l&#39;&#201;diteur XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'Éditeur XML offre des fonctionnalités IntelliSense complètes comparables à celles d'autres éditeurs de langage fournis dans Visual Studio.Cette section explique comment vous pouvez utiliser IntelliSense avec des documents en langage XSD \(XML Schema Definition\) et XSLT.  
  
## IntelliSense dans un document XSD  
 Une fois qu'un schéma est associé à votre document, vous obtenez une liste déroulante d'éléments attendus chaque fois que vous entrez `"<"` ou que vous cliquez sur le bouton **Afficher la liste des membres objets** dans la barre d'outils de l'Éditeur XML.Pour plus d'informations sur l'association de schémas à vos documents XML, consultez [Validation de documents XML](../xml-tools/xml-document-validation.md).  
  
 Lorsque vous entrez un Espace dans une balise de début, vous obtenez également une liste déroulante de tous les attributs qui peuvent être ajoutés à l'élément actuel.  
  
 Lorsque vous entrez `"="` pour une valeur d'attribut ou que vous insérez le guillemet ouvrant introduisant cette valeur, vous obtenez également une liste des valeurs possibles pour cet attribut.Des valeurs ne sont proposées que lorsque le schéma fournit une énumération de valeurs via des facettes `xsd:enumeration` ou que l'attribut est de type `Boolean`.Une liste IntelliSense de codes de langage connus est également fournie pour `xml:lang` ou pour tout `simpleType` dérivant de `xsd:language`.Une liste IntelliSense des valeurs `targetNamespace` connues est fournie pour les déclarations d'espaces de noms.  
  
 Une liste IntelliSense des valeurs possibles est également fournie lorsque vous entrez `">"` pour fermer une balise de début si l'élément est de type `simpleType`.Le comportement des éléments est similaire à celui des attributs décrits dans le paragraphe précédent.  
  
 Des info\-bulles s'affichent également dans les listes IntelliSense, d'après les informations `xsd:annotation` et `xsd:documentation` trouvées dans le schéma associé.  
  
## IntelliSense dans un document XSLT  
 Après avoir ajouté un modèle nommé ou un attribut à votre document XSLT, vous pouvez utiliser IntelliSense pour insérer les éléments suivants :  
  
-   Noms d'ensemble d'attributs.  
  
-   Modes de modèle.  
  
-   Noms de modèle.  
  
-   Noms de paramètre pour un mode donné.  
  
-   Noms de paramètre pour un modèle nommé donné.  
  
 Pour plus d'informations, consultez la rubrique [Procédure pas à pas : utilisation d'IntelliSense XSLT](../xml-tools/walkthrough-using-xslt-intellisense.md).  
  
## Saisie semi\-automatique  
 L'Éditeur XML facilite également l'édition du XML en complétant automatiquement la syntaxe XML requise.Par exemple, si vous entrez la balise de début suivante :  
  
 `<book>`  
  
 L'éditeur XML insère la balise de fin et place le curseur juste après la balise de début.Voici un exemple de cette fonctionnalité \(le signe « &#124; » indique la position du curseur\) :  
  
 `<book>`&#124;`</book>`  
  
 Étant donné que les valeurs des attributs doivent toujours être placées entre guillemets, l'éditeur XML insère automatiquement ces guillemets.Par exemple, si vous entrez :  
  
 `<book title=`  
  
 L'éditeur XML ajoute les guillemets et place le curseur entre ces guillemets :  
  
 `<book title="`&#124;`"`  
  
 De même, l'éditeur XML insère automatiquement la syntaxe XML suivante :  
  
-   Fin d'une instruction de traitement : `?>`  
  
-   Fin d'un bloc CDATA : `]]>`  
  
-   Fin d'un commentaire : `-->`  
  
-   Fin d'une déclaration DTD : `>`  
  
 L'éditeur XML offre également la possibilité d'insérer une déclaration d'espace de noms si vous sélectionnez un attribut ou un élément qualifié d'un espace de noms à partir d'une liste IntelliSense alors que l'espace de noms de cet élément ou attribut ne figure pas encore dans la portée.  
  
 Par exemple, si vous sélectionnez l'élément `e:Book` dans la liste IntelliSense, sachant que le préfixe est lié à l'espace de noms `http://books` qui n'a pas encore été déclaré dans le document, l'éditeur XML insère automatiquement la déclaration d'espace de noms requise.Il en résulte le texte XML suivant :  
  
 `<e:Book xmlns:e="http://books"`  
  
## Accolades correspondantes  
 L'éditeur XML met en évidence les accolades pour indiquer immédiatement quel élément vous venez de fermer.Vous pouvez également utiliser le raccourci clavier \(CTRL\+\]\) pour passer d'une accolade à son correspondant.  
  
 L'éditeur XML offre cette fonctionnalité pour les éléments suivants :  
  
-   Les balises de début et de fin qui se correspondent  
  
-   Toute paire de crochets « \< » ou « \> »  
  
-   Le début et la fin de commentaires  
  
-   Le début et la fin d'instructions de traitement  
  
-   Le début et la fin de blocs CDATA  
  
-   Le début et la fin de déclarations DTD  
  
-   Les guillemets ouvrants et fermants des attributs  
  
## Modification des options IntelliSense  
 Les fonctions IntelliSense et de saisie semi\-automatique sont activées par défaut.Vous pouvez toutefois modifier cette sélection par défaut en changeant les paramètres dans Outils\\Options.  
  
 La section **Insertion automatique** de la page **Divers** contrôle le comportement suivant :  
  
|Nom|Description|  
|---------|-----------------|  
|Balises de fermeture|Insère des balises de fermeture pour les nouveaux éléments.|  
|Guillemets d'attribut|Insère les guillemets marquant une valeur d'attribut lorsque vous entrez un nouveau nom d'attribut.|  
|Autre balisage|Complète les commentaires, CDATA, DOCTYPE, instructions de traitement et autres déclarations de balisage.|  
  
#### Pour modifier le comportement de la saisie semi\-automatique  
  
1.  Sélectionnez **Options** dans le menu **Outils**.  
  
2.  Développez **Éditeur de texte**, puis **XML** et sélectionnez **Divers**.  
  
3.  Apportez les modifications voulues à la section **Insertion automatique** et cliquez sur **OK**.  
  
## Voir aussi  
 [Éditeur XML](../xml-tools/xml-editor.md)   
 [Utilisation de la fonctionnalité IntelliSense](../ide/using-intellisense.md)   
 [Procédure pas à pas : utilisation d'IntelliSense XSLT](../xml-tools/walkthrough-using-xslt-intellisense.md)