---
title: Fonctionnalités IntelliSense de l’éditeur XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b8299e96f6ec074ce82dcd1fd872e56886c2d19b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953929"
---
# <a name="xml-editor-intellisense-features"></a>Fonctionnalités IntelliSense de l'Éditeur XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
L’Éditeur XML offre des fonctionnalités IntelliSense complètes comparables à celles d’autres éditeurs de langage fournis dans Visual Studio. Cette section explique comment vous pouvez utiliser IntelliSense avec des documents en langage XSD (XML Schema Definition) et XSLT.  
  
## <a name="intellisense-in-an-xsd-document"></a>IntelliSense dans un document XSD  
 Une fois un schéma est associé à votre document, vous obtenez une liste déroulante d’éléments attendus chaque fois que vous tapez `"<"` ou cliquez sur le **afficher une liste des membres objets** bouton sur la barre d’outils de l’éditeur XML. Pour plus d’informations sur la façon d’associer des schémas à vos documents XML, consultez [Validation de documents XML](../xml-tools/xml-document-validation.md).  
  
 Lorsque vous entrez un ESPACE dans une étiquette de début, vous obtenez également une liste déroulante de tous les attributs qui peuvent être ajoutés à l’élément actuel.  
  
 Lorsque vous entrez `"="` pour une valeur d'attribut ou que vous insérez le guillemet ouvrant introduisant cette valeur, vous obtenez également une liste des valeurs possibles pour cet attribut. Des valeurs ne sont proposées que lorsque le schéma fournit une énumération de valeurs via des facettes `xsd:enumeration` ou que l'attribut est de type `Boolean`. Une liste IntelliSense de codes de langage connus est également fournie pour `xml:lang` ou pour tout `simpleType` dérivant de `xsd:language`. Une liste IntelliSense des valeurs `targetNamespace` connues est fournie pour les déclarations d'espaces de noms.  
  
 Une liste IntelliSense des valeurs possibles est également fournie lorsque vous entrez `">"` pour fermer une balise de début si l'élément est de type `simpleType`. Le comportement des éléments est similaire à celui des attributs décrits dans le paragraphe précédent.  
  
 Des info-bulles s'affichent également dans les listes IntelliSense, d'après les informations `xsd:annotation` et `xsd:documentation` trouvées dans le schéma associé.  
  
## <a name="intellisense-in-an-xslt-document"></a>IntelliSense dans un document XSLT  
 Après avoir ajouté un modèle nommé ou un attribut à votre document XSLT, vous pouvez utiliser IntelliSense pour insérer les éléments suivants :  
  
- Noms d'ensemble d'attributs.  
  
- Modes de modèle.  
  
- Noms de modèle.  
  
- Noms de paramètre pour un mode donné.  
  
- Noms de paramètre pour un modèle nommé donné.  
  
  Pour plus d’informations, consultez [Procédure pas à pas : Utilisation d’IntelliSense XSLT](../xml-tools/walkthrough-using-xslt-intellisense.md) rubrique.  
  
## <a name="auto-completion"></a>Remplissage automatique  
 L'éditeur XML facilite également l'édition du XML en complétant automatiquement la syntaxe XML requise. Par exemple, si vous entrez l’étiquette de début suivante :  
  
 `<book>`  
  
 L’éditeur XML insère l’étiquette de fin et place le curseur juste après l’étiquette de début. Voici un exemple de ce (le «&#124;» indique la position du curseur) :  
  
 `<book>`&#124;`</book>`  
  
 Étant donné que les valeurs des attributs doivent toujours être placées entre guillemets, l'éditeur XML insère automatiquement ces guillemets. Par exemple, si vous entrez :  
  
 `<book title=`  
  
 L'éditeur XML ajoute les guillemets et place le curseur entre ces guillemets :  
  
 `<book title="`&#124;`"`  
  
 De même, l'éditeur XML insère automatiquement la syntaxe XML suivante :  
  
- Fin d'une instruction de traitement : `?>`  
  
- Fin d'un bloc CDATA : `]]>`  
  
- Fin d'un commentaire : `-->`  
  
- Fin d'une déclaration DTD : `>`  
  
  L'éditeur XML offre également la possibilité d'insérer une déclaration d'espace de noms si vous sélectionnez un attribut ou un élément qualifié d'un espace de noms à partir d'une liste IntelliSense alors que l'espace de noms de cet élément ou attribut ne figure pas encore dans la portée.  
  
  Par exemple, si vous sélectionnez l'élément `e:Book` dans la liste IntelliSense, sachant que le préfixe est lié à l'espace de noms `http://books` qui n'a pas encore été déclaré dans le document, l'éditeur XML insère automatiquement la déclaration d'espace de noms requise. Il en résulte le texte XML suivant :  
  
  `<e:Book xmlns:e="http://books"`  
  
## <a name="brace-matching"></a>Accolades correspondantes  
 L'éditeur XML met en évidence les accolades pour indiquer immédiatement quel élément vous venez de fermer. Vous pouvez également utiliser le raccourci clavier (CTRL+]) pour passer d'une accolade à son correspondant.  
  
 L'éditeur XML offre cette fonctionnalité pour les éléments suivants :  
  
-   Les étiquettes de début et de fin qui se correspondent.  
  
-   Toute paire de «\<» ou « > » crochets pointus.  
  
-   Le début et la fin de commentaires  
  
-   Le début et la fin d'instructions de traitement  
  
-   Le début et la fin de blocs CDATA  
  
-   Le début et la fin de déclarations DTD  
  
-   Les guillemets ouvrants et fermants des attributs  
  
## <a name="modifying-the-intellisense-options"></a>Modification des options IntelliSense  
 Les fonctions IntelliSense et de saisie semi-automatique sont activées par défaut. Vous pouvez toutefois modifier cette sélection par défaut en changeant les paramètres dans Outils\Options.  
  
 Le **insertion automatique** section de la **divers** page contrôle le comportement suivant :  
  
|Nom|Description|  
|----------|-----------------|  
|Balises de fermeture|Insère des étiquettes de fermeture pour les nouveaux éléments.|  
|Guillemets d'attribut|Insère les guillemets marquant une valeur d'attribut lorsque vous entrez un nouveau nom d'attribut.|  
|Autre balisage|Complète les commentaires, CDATA, DOCTYPE, instructions de traitement et autres déclarations de balisage.|  
  
#### <a name="to-change-the-auto-completion-behavior"></a>Pour modifier le comportement de la saisie semi-automatique  
  
1.  Sélectionnez **Options** dans le menu **Outils**.  
  
2.  Développez **éditeur de texte**, développez **XML**, puis sélectionnez **divers**.  
  
3.  Apporter des modifications à la **insertion automatique** section et cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur XML](../xml-tools/xml-editor.md)   
 [Utilisation de la fonctionnalité IntelliSense](../ide/using-intellisense.md)   
 [Procédure pas à pas : Utilisation d’IntelliSense XSLT](../xml-tools/walkthrough-using-xslt-intellisense.md)
