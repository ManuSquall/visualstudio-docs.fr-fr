---
title: "Personnalisation du stockage de fichiers et de la s&#233;rialisation XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.xmlbehavior"
helpviewer_keywords: 
  - "Domain-Specific Language, sérialisation"
ms.assetid: 76c53ef1-e3b9-45da-b425-1bddb3c01395
caps.latest.revision: 17
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 17
---
# Personnalisation du stockage de fichiers et de la s&#233;rialisation XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque l’utilisateur enregistre une instance, ou *modèle*, d’un langage spécifique à un domaine (DSL) dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], un fichier XML est créé ou mis à jour. Le fichier peut être rechargé pour recréer le modèle dans le magasin.  
  
 Vous pouvez personnaliser le schéma de sérialisation en réglant les paramètres sous **comportement de sérialisation Xml** dans l’Explorateur DSL. Il existe un nœud sous **comportement de sérialisation Xml** pour chaque classe de domaine, la propriété et la relation. Les relations sont situées sous leurs classes de source. Il existe également des nœuds correspondant à la forme, connecteur et les classes de schéma.  
  
 Vous pouvez également écrire du code de programme pour une personnalisation avancée.  
  
> [!NOTE]
>  Si vous souhaitez enregistrer le modèle dans un format particulier, mais vous n’êtes pas obligé de recharger à partir de ce formulaire, envisagez d’utiliser des modèles de texte pour générer la sortie à partir du modèle, au lieu d’une méthode de sérialisation personnalisée. Pour plus d’informations, consultez [génération du Code à partir d’un langage spécifique au domaine](../modeling/generating-code-from-a-domain-specific-language.md).  
  
## <a name="model-and-diagram-files"></a>Fichiers de modèle et diagramme  
 Chaque modèle est généralement enregistré dans deux fichiers :  
  
-   Le fichier de modèle a un nom tel que **Model1.mydsl**. Il stocke les éléments de modèle et les relations et leurs propriétés. L’extension de fichier comme **.mydsl** est déterminée par la **FileExtension** propriété de la **éditeur** nœud dans la définition DSL.  
  
-   Le fichier de diagramme a un nom tel que **Model1.mydsl.diagram**. Il stocke les formes, connecteurs et leurs positions, couleurs, épaisseurs et autres détails de l’apparence du diagramme. Si l’utilisateur supprime un **.diagram** fichier, les informations essentielles dans le modèle ne sont pas perdues. Uniquement à la disposition du diagramme est perdue. Lorsque le fichier de modèle est ouvert, une valeur par défaut définie de formes et connecteurs seront créées.  
  
#### <a name="to-change-the-file-extension-of-a-dsl"></a>Pour modifier l’extension de fichier d’un DSL  
  
1.  Ouvrez la définition DSL. Dans l’Explorateur DSL, cliquez sur le nœud de l’éditeur.  
  
2.  Dans la fenêtre Propriétés, modifiez la **FileExtension** propriété. N’incluez pas la première «. » de l’extension de nom de fichier.  
  
3.  Dans l’Explorateur de solutions, remplacez le nom des fichiers de modèle de deux éléments dans **DslPackage\ProjectItemTemplates**. Ces fichiers ont des noms qui suivent ce format :  
  
     `myDsl.diagram`  
  
     `myDsl.myDsl`  
  
## <a name="the-default-serialization-scheme"></a>La méthode de sérialisation par défaut  
 Pour créer un exemple de cette rubrique, la définition DSL suivante a été utilisée.  
  
 ![Diagramme de définition DSL &#45 ; modèle d’arbre généalogique](../modeling/media/familyt_person.png "FamilyT_Person")  
  
 Cette solution DSL a été utilisé pour créer un modèle qui a l’apparence suivante sur l’écran.  
  
 ![Diagramme d’arbre généalogique, boîte à outils et explorateur](../modeling/media/familyt_instance.png "FamilyT_Instance")  
  
 Ce modèle a été enregistré et ouvert dans l’éditeur de texte XML :  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">  
  <people>  
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">  
      <children>  
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />  
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />  
      </children>  
    </person>  
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />  
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />  
  </people>  
</familyTreeModel>  
  
```  
  
 Notez les points suivants concernant le modèle sérialisé :  
  
-   Chaque nœud XML a un nom qui est identique à un nom de classe de domaine, sauf que la première lettre est en minuscule. Par exemple, `familyTreeModel` et `person`.  
  
-   Propriétés de domaine tels que le nom et l’année de naissance sont sérialisées en tant qu’attributs dans les nœuds XML. Là encore, le premier caractère du nom de la propriété est converti en minuscules.  
  
-   Chaque relation est sérialisée comme un nœud XML imbriqué à l’intérieur de la terminaison source de la relation. Le nœud a le même nom que la propriété du rôle source, mais avec une initiale minuscule.  
  
     Par exemple, dans la définition DSL, un rôle nommé **personnes** vient à le **FamilyTree** (classe).  Dans le XML, il est représenté par le nœud nommé `people` imbriqué dans le `familyTreeModel` nœud.  
  
-   La terminaison cible de chaque relation d’incorporation est sérialisée en tant que nœud imbriqué sous la relation. Par exemple, le `people` nœud contient plusieurs `person` nœuds.  
  
-   La terminaison cible de chaque relation de référence est sérialisée comme un *moniker*, qui encode une référence à l’élément cible.  
  
     Par exemple, sous un `person` nœud, il peut y avoir un `children` relation. Ce nœud contient les monikers telles que :  
  
    ```  
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />  
    ```  
  
## <a name="understanding-monikers"></a>Présentation des Monikers  
 Monikers sont utilisés pour représenter des références croisées entre les différentes parties des fichiers de modèle et de diagramme. Elles sont également utilisées dans le `.diagram` pour faire référence aux nœuds dans le fichier de modèle. Il existe deux formes de moniker :  
  
-   *Les monikers ID* citer le GUID de l’élément cible. Exemple :  
  
    ```  
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />  
  
    ```  
  
-   *Qualifié monikers clés* identifier l’élément cible par la valeur d’une propriété de domaine désigné appelée la clé de moniker. Le moniker de l’élément cible est préfixé par le moniker de son élément parent dans l’arborescence de relations d’incorporation.  
  
     Les exemples suivants sont stockés dans un langage DSL dans lequel il est une classe de domaine nommée Album, ce qui a une relation d’incorporation à un domaine nommé chanson de classe :  
  
    ```  
    <albumMoniker title="/My Favorites/Jazz after Teatime" />  
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
  
    ```  
  
     Monikers clés qualifiés seront utilisées si la classe cible possède une propriété de domaine pour lequel l’option **est la clé de Moniker** a la valeur `true` dans **comportement de sérialisation Xml**. Dans l’exemple, cette option est définie pour les propriétés de domaine nommées « Title » dans les classes de domaine « Album » et « Morceau ».  
  
 Monikers clés qualifiés sont plus faciles à lire que les monikers ID. Si vous envisagez le XML de vos fichiers de modèle à être lues par des personnes, envisagez l’utilisation de monikers clés qualifiés. Toutefois, il est possible pour l’utilisateur de définir plusieurs éléments à avoir la même clé de moniker. Clés dupliquées peut provoquer le fichier ne pas à recharger correctement. Par conséquent, si vous définissez une classe de domaine qui est référencée à l’aide de monikers clés qualifiés, vous devez envisager les façons d’empêcher l’utilisateur d’enregistrer un fichier contenant des noms en double.  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Pour définir une classe de domaine devant être référencé par des monikers ID  
  
1.  Assurez-vous que **est la clé de Moniker** est `false` pour chaque propriété de domaine dans la classe et ses classes de base.  
  
    1.  Dans l’Explorateur DSL, développez **données Behavior\Class de sérialisation Xml\\***\< la classe de domaine>***\Element données**.  
  
    2.  Vérifiez que **est la clé de Moniker** est `false` pour chaque propriété de domaine.  
  
    3.  Si la classe de domaine a une classe de base, répétez la procédure décrite dans cette classe.  
  
2.  Définissez **Id de sérialisation** = `true` pour la classe de domaine.  
  
     Cette propriété se trouve sous **comportement de sérialisation Xml**.  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Pour définir une classe de domaine devant être référencé par des monikers clés qualifiés  
  
-   Définissez **est la clé de Moniker** pour une propriété de domaine d’une classe de domaine existants. Le type de la propriété doit être `string`.  
  
    1.  Dans l’Explorateur DSL, développez **données Behavior\Class de sérialisation Xml\\***\< la classe de domaine>***\Element données**, puis sélectionnez la propriété de domaine.  
  
    2.  Dans la fenêtre Propriétés, définissez **est la clé de Moniker** à `true`.  
  
-   \- ou -  
  
     Créer une nouvelle classe de domaine à l’aide du **classe de domaine nommé** outil.  
  
     Cet outil crée une nouvelle classe qui possède une propriété de domaine appelée nom. Le **nom de l’élément est** et **est la clé de Moniker** Propriétés de cette propriété de domaine sont initialisées à `true`.  
  
-   \- ou -  
  
     Créer une relation d’héritage à partir de la classe de domaine à une autre classe qui a une propriété de clé de moniker.  
  
### <a name="avoiding-duplicate-monikers"></a>Prévention des Monikers en double  
 Si vous utilisez des monikers clés complets, il est possible que deux éléments dans un modèle utilisateur peut avoir la même valeur dans la propriété de clé. Par exemple, si votre DSL possède une classe Person qui a une propriété de nom, l’utilisateur peut définir les noms de deux éléments doivent être identiques. Bien que le modèle peut être enregistré dans le fichier, il serait recharge pas correctement.  
  
 Il existe plusieurs méthodes qui permettent d’éviter cette situation :  
  
-   Définissez **nom de l’élément est** = `true` pour la propriété de clé de domaine. Sélectionnez la propriété de domaine sur le diagramme de définition DSL, puis définissez la valeur dans la fenêtre Propriétés.  
  
     Lorsque l’utilisateur crée une nouvelle instance de la classe, cette valeur, la propriété de domaine à affecter automatiquement une valeur différente. Le comportement par défaut ajoute un nombre à la fin du nom de classe. Cela n’empêche pas l’utilisateur de modifier le nom à un doublon, mais il permet le cas lorsque l’utilisateur ne définit pas la valeur avant d’enregistrer le modèle.  
  
-   Activer la validation de la solution DSL. Dans l’Explorateur DSL, sélectionnez éditeur\validation et définissez la **utilise...** propriétés `true`.  
  
     Il existe une méthode de validation générée automatiquement qui vérifie pour les ambiguïtés. La méthode se trouve dans le `Load` catégorie de validation. Cela permet de s’assurer que l’utilisateur est averti qu’il ne pourrait pas être possible de rouvrir le fichier.  
  
     Pour plus d’informations, consultez [Validation dans un langage spécifique au domaine](../modeling/validation-in-a-domain-specific-language.md).  
  
### <a name="moniker-paths-and-qualifiers"></a>Les qualificateurs et les chemins d’accès de moniker  
 Un moniker clé qualifié se termine par la clé de moniker et est préfixé avec le nom de son parent dans l’arborescence d’incorporation. Par exemple, si le moniker d’un Album est :  
  
```  
<albumMoniker title="/My Favorites/Jazz after Teatime" />  
  
```  
  
 Une des morceaux de cet Album peut être :  
  
```  
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
```  
  
 Toutefois, si au lieu de cela, les Albums sont référencées par ID, puis les monikers serait comme suit :  
  
```  
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />  
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />  
```  
  
 Notez qu’un GUID étant unique, il est jamais préfixé par le moniker de son parent.  
  
 Si vous savez qu’une propriété de domaine particulier aura toujours une valeur unique dans un modèle, vous pouvez définir **est un qualificateur de Moniker** à `true` pour cette propriété. Cela entraîne son utilisation en tant que qualificateur, sans utiliser le moniker du parent. Par exemple, si vous définissez à la fois **est un qualificateur de Moniker** et **est la clé de Moniker** pour la propriété de domaine de titre de la classe Album, nom ou l’identificateur du modèle est inutilisé dans monikers Album et ses enfants incorporés :  
  
```  
<albumMoniker name="Jazz after Teatime" />  
<songMoniker title="/Jazz after Teatime/Hot tea" />  
  
```  
  
## <a name="customizing-the-structure-of-the-xml"></a>Personnalisation de la structure du document XML  
 Pour effectuer les personnalisations suivantes, développez la **comportement de sérialisation Xml** nœud dans l’Explorateur DSL. Dans une classe de domaine, développez le nœud de données de l’élément pour afficher la liste des propriétés et des relations qui sont générées à cette classe. Sélectionnez une relation et ajustez ses options dans la fenêtre Propriétés.  
  
-   Définissez **omettre un élément** sur true pour ignorer le nœud de rôle source, en laissant uniquement la liste des éléments cibles. Vous ne devez pas définir cette option s’il existe plusieurs relations entre les classes source et cible.  
  
    ```  
  
    <familyTreeModel ...>  
      <!-- The following node is omitted by using Omit Element: -->  
      <!-- <people> -->  
        <person name="Henry VIII" .../>  
        <person name="Elizabeth I" .../>  
      <!-- </people> -->  
    </familyTreeModel>  
  
    ```  
  
-   Définissez **utiliser le formulaire complet** pour incorporer les nœuds cibles dans des nœuds représentant les instances de relation. Cette option est définie automatiquement lorsque vous ajoutez des propriétés de domaine à une relation de domaine.  
  
    ```  
  
    <familyTreeModel ...>  
      <people>  
        <!-- The following node is inserted by using Use Full Form: -->  
        <familyTreeModelHasPeople myRelationshipProperty="x1">  
          <person name="Henry VIII" .../>  
        </familyTreeModelHasPeople>  
        <familyTreeModelHasPeople myRelationshipProperty="x2">  
          <person name="Elizabeth I" .../>  
        </familyTreeModelHasPeople>  
      </people>  
    </familyTreeModel>  
  
    ```  
  
-   Définissez **représentation** = **élément** d’avoir une propriété de domaine enregistrée en tant qu’élément plutôt que comme une valeur d’attribut.  
  
    ```  
    <person name="Elizabeth I" birthYear="1533">  
      <deathYear>1603</deathYear>  
    </person>  
    ```  
  
-   Pour modifier l’ordre dans lequel les attributs et les relations sont sérialisées, cliquez sur un élément sous l’élément de données et utiliser le **Monter** ou **Descendre** commandes de menu.  
  
## <a name="major-customization-using-program-code"></a>Personnalisation principales à l’aide de code de programme  
 Vous pouvez remplacer la partie ou l’ensemble des algorithmes de sérialisation.  
  
 Nous recommandons que vous étudiez le code dans **Dsl\Generated Code\Serializer.cs** et **SerializationHelper.cs**.  
  
#### <a name="to-customize-the-serialization-of-a-particular-class"></a>Pour personnaliser la sérialisation d’une classe particulière  
  
1.  Définissez **personnalisé est** dans le nœud pour cette classe sous **comportement de sérialisation Xml**.  
  
2.  Transformer tous les modèles, générez la solution et examiner les erreurs de compilation qui en résulte. Commentaires de près de chaque erreur expliquent le code que vous devez fournir.  
  
#### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Pour fournir votre propre sérialisation pour l’ensemble du modèle  
  
1.  Substituer des méthodes dans Dsl\GeneratedCode\SerializationHelper.cs  
  
## <a name="options-in-xml-serialization-behavior"></a>Options de comportement de sérialisation Xml  
 Dans l’Explorateur DSL, le nœud de comportement de sérialisation Xml contient un nœud enfant pour chaque classe de domaine, relation, forme, connecteur et de classe de diagramme. Sous chacun de ces nœuds est une liste de propriétés et relations ayant cet élément. Les relations sont représentées dans leur propre droit et sous leurs classes de source.  
  
 Le tableau suivant récapitule les options que vous pouvez définir dans cette section de la définition DSL. Dans chaque cas, sélectionnez un élément dans l’Explorateur DSL et définir les options dans la fenêtre Propriétés.  
  
### <a name="xml-class-data"></a>Données XML (classe)  
 Ces éléments ont été trouvés dans l’Explorateur DSL sous **données Behavior\Class de sérialisation Xml**.  
  
|||  
|-|-|  
|Propriété|Description|  
|Schéma de l’élément personnalisé|Si la valeur est True, indique que la classe de domaine dispose d’un schéma de l’élément personnalisé|  
|Personnalisé|Affectez la valeur **True** Si vous souhaitez écrire votre propre code de sérialisation et de désérialisation pour cette classe de domaine.<br /><br /> Générez la solution et examinez les erreurs pour découvrir des instructions détaillées.|  
|Classe de domaine|Classe de domaine auquel s’applique ce nœud de données de classe. Lecture seule.|  
|Nom de l'élément|Nom du nœud XML pour les éléments de cette classe. La valeur par défaut est une version en minuscules du nom de classe de domaine.|  
|Nom de l’attribut moniker|Nom de l’attribut utilisé dans les éléments de moniker pour contenir la référence. Si elle est vide, le nom de la propriété de clé ou un id est utilisé.<br /><br /> Dans cet exemple, il est « name » :  `<personMoniker name="/Mike Nash"/>`|  
|Nom de l’élément moniker|Nom de l’élément xml utilisé pour les monikers qui font référence aux éléments de cette classe.<br /><br /> La valeur par défaut est une version en minuscules du nom de classe possède le suffixe « Nom ». Par exemple, `personMoniker`.|  
|Nom de Type de moniker|Nom du type xsd généré des monikers aux éléments de cette classe. Le schéma XSD est **Dsl\Generated Code\\\*Schema.xsd**|  
|Sérialiser du code|Si la valeur est True, le GUID de l’élément est inclus dans le fichier. Cela doit être true s’il n’existe aucune propriété marquée **est la clé de Moniker** et DSL définit les relations de référence à cette classe.|  
|Nom de type|Nom du type xml généré dans le xsd à partir de la classe de domaine désigné.|  
|Notes|Remarques informelles associées à cet élément|  
  
### <a name="xml-property-data"></a>Données de la propriété XML  
 Nœuds de la propriété XML sont trouvent sous les nœuds de la classe.  
  
|||  
|-|-|  
|Propriété|Description|  
|Propriété de domaine|Propriété à laquelle les données de configuration de sérialisation xml s’applique. Lecture seule.|  
|Est la clé de Moniker|Si la valeur est True, la propriété est utilisée comme clé pour la création des monikers référençant des instances de cette classe de domaine.|  
|Qualificateur de Moniker|Si la valeur est True, la propriété est utilisée pour créer le qualificateur dans monikers. Si la valeur false et si SerializeId n’est pas valable pour cette classe de domaine, des monikers sont qualifiés par le nom de l’élément parent dans l’arborescence d’incorporation.|  
|Représentation sous forme de|Si l’attribut, la propriété est sérialisé comme un attribut xml ; Si l’élément, il est sérialisé comme un élément ; Si Ignorer, il n’est pas sérialisé.|  
|Nom XML|Nom utilisé pour l’élément qui représente la propriété ou un attribut xml. Par défaut, il s’agit d’une version en minuscules du nom de propriété de domaine.|  
|Notes|Remarques informelles associées à cet élément|  
  
### <a name="xml-role-data"></a>Données de rôle de XML  
 Les nœuds de données de rôle sont trouvent sous les nœuds de la classe source.  
  
|Propriété|Description|  
|--------------|-----------------|  
|A Moniker personnalisé|Définissez cette propriété sur true si vous souhaitez fournir votre propre code pour la génération et la résolution des monikers qui passent par cette relation.<br /><br /> Pour obtenir des instructions détaillées, générez la solution, puis double-cliquez sur les messages d’erreur.|  
|Relation de domaine|Spécifie la relation à laquelle ces options s’appliquent. Lecture seule.|  
|Omettre l’élément|Si la valeur est true, le nœud XML qui correspond au rôle source est omis à partir du schéma.<br /><br /> S’il existe plusieurs relations entre les classes source et cible, ce nœud de rôle fait la distinction entre les liens qui appartiennent aux relations entre les deux. Par conséquent, nous recommandons que vous ne définissez pas cette option dans ce cas.|  
|Nom d’élément de rôle|Spécifie le nom de l’élément XML qui est dérivée de rôle source. La valeur par défaut est le nom de propriété du rôle.|  
|Plein écran|Si la valeur est true, chaque élément de la cible ou le moniker est placé dans un nœud XML représentant la relation. Cela doit être défini sur true si la relation a ses propres propriétés de domaine.|  
  
## <a name="see-also"></a>Voir aussi  
 [Navigation et mise à jour d’un modèle de Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Génération de Code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md)