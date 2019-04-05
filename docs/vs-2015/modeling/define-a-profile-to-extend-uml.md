---
title: Définir un profil pour étendre UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- profiles, UML
- stereotypes, UML
- UML, profiles and stereotypes
- UML - extending, defining profiles
- UML, customizing
- UML, profiles
ms.assetid: 776589cb-f89d-48d5-aafa-04a4c074b0d6
caps.latest.revision: 44
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 832b7b148e73e8d21d56dea6b676910019294e13
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949293"
---
# <a name="define-a-profile-to-extend-uml"></a>Définir un profil pour étendre UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez définir un *profil UML* pour personnaliser les éléments de modèle standard à des fins spécifiques. Un profil définit un ou plusieurs *stéréotypes UML*. Un stéréotype permet de marquer un type comme représentant un genre d'objet particulier. Un stéréotype peut également étendre la liste de propriétés d'un élément.  
  
 Plusieurs profils sont installés avec les éditions prises en charge de Visual Studio. Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Prise en charge des versions pour les outils d'architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport). Pour plus d’informations sur ces profils et sur la façon d’appliquer des stéréotypes, consultez [personnaliser votre modèle avec des profils et stéréotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md).  
  
 Vous pouvez définir vos propres profils pour adapter et étendre UML à votre propre secteur d'activité ou architecture. Exemple :  
  
- Si vous définissez fréquemment des sites web, vous pouvez définir votre propre profil qui fournit un stéréotype « Pageweb » qui peut être appliqué aux classes dans les diagrammes de classes. Vous pouvez ensuite utiliser des diagrammes de classes pour planifier un site web. Chaque classe « Pageweb » aurait des propriétés supplémentaires pour le contenu de la page, le style et ainsi de suite.  
  
- Si vous développez des logiciels d'opérations bancaires, vous pouvez définir un profil qui fournit un stéréotype « Compte ». Vous pouvez ensuite utiliser des diagrammes de classes pour définir différents types de comptes et afficher les relations entre eux.  
  
  Vous pouvez distribuer vos propres profils à votre équipe. Chaque membre de l'équipe peut installer votre profil. Cela leur permet de modifier et de créer des modèles qui utilisent ses stéréotypes.  
  
> [!NOTE]
>  Si vous appliquez les stéréotypes d'un profil dans un modèle que vous modifiez et que vous partagez ensuite le modèle avec d'autres personnes, elles doivent installer le même profil sur leurs propres ordinateurs. Dans le cas contraire, elles ne pourront pas voir les stéréotypes que vous avez utilisés.  
  
 Un profil fait souvent partie d’une plus grande [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] extension. Par exemple, vous pouvez définir une commande qui traduit certaines parties d'un modèle en code. Vous pouvez définir un profil que les utilisateurs doivent appliquer aux packages qu'ils souhaitent traduire. Vous devez dans ce cas distribuer votre nouvelle commande avec le profil dans une extension [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] unique.  
  
 Vous pouvez aussi définir des variantes localisées d'un profil. Les utilisateurs chargeant votre extension voient la variante correspondant à leur propre culture.  
  
##  <a name="DefineProfile"></a> Comment définir un profil  
  
#### <a name="to-define-a-uml-profile"></a>Pour définir un profil UML  
  
1.  Créez un fichier XML avec l'extension de nom de fichier `.profile`.  
  
2.  Ajouter des définitions de stéréotypes en respectant les instructions décrites dans [la Structure d’un profil](#Schema).  
  
3.  Ajoutez le profil à une Extension Visual Studio (fichier `.vsix`). Vous pouvez créer une extension pour votre profil ou ajouter le profil à une extension existante.  
  
     Consultez la section suivante, [comment ajouter un profil à une Extension Visual Studio](#AddProfile).  
  
4.  Installez l'extension sur votre ordinateur.  
  
    1.  Double-cliquez sur le fichier d'extension, dont l'extension de nom de fichier est `.vsix`.  
  
    2.  Redémarrez Visual Studio.  
  
5.  Vérifiez que le profil a été installé.  
  
    1.  Sélectionnez le modèle dans l'Explorateur UML.  
  
    2.  Dans la fenêtre Propriétés, cliquez sur le **profils** propriété. Votre profil apparaît dans le menu. Cochez la case en regard du profil.  
  
    3.  Sélectionnez un élément pour lequel votre profil définit des stéréotypes. Dans la fenêtre Propriétés, cliquez sur le **stéréotypes** propriété. Vos stéréotypes apparaissent dans la liste. Cochez la case en regard de l'un des stéréotypes.  
  
    4.  Si votre profil définit des propriétés supplémentaires pour ce stéréotype, développez la propriété du stéréotype pour les afficher.  
  
6.  Envoyez le fichier d'extension à d'autres utilisateurs de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour qu'ils l'installent sur leurs ordinateurs.  
  
##  <a name="AddProfile"></a> Comment ajouter un profil à une Extension Visual Studio  
 Pour installer un profil et pouvoir l'envoyer à d'autres utilisateurs, vous devez ajouter le profil à une Extension Visual Studio. Pour plus d’informations, consultez [déploiement d’Extensions Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160780).  
  
#### <a name="to-define-a-profile-in-a-new-visual-studio-extension"></a>Pour définir un profil dans une nouvelle Extension Visual Studio  
  
1. Créez un projet d'Extension Visual Studio.  
  
   > [!NOTE]
   >  Pour appliquer cette procédure, vous devez avoir installé [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
   1.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
   2.  Dans le **nouveau projet** boîte de dialogue **modèles installés**, développez **Visual C#**, cliquez sur **extensibilité**, puis cliquez sur  **Projet VSIX**. Définissez le nom du projet et cliquez sur **OK**.  
  
2. Ajoutez votre profil au projet.  
  
   -   Dans l’Explorateur de solutions, cliquez sur le projet, pointez sur **ajouter**, puis cliquez sur **élément existant**. Dans la boîte de dialogue, recherchez votre fichier de profil.  
  
3. Définissez le fichier de profil **copier dans la sortie** propriété.  
  
   1.  Dans l’Explorateur de solutions, cliquez sur le fichier de profil, puis cliquez sur **propriétés**.  
  
   2.  Dans la fenêtre Propriétés, définissez la **Copy to Output Directory** propriété **toujours copier**.  
  
4. Dans l'Explorateur de solutions, ouvrez `source.extension.vsixmanifest`.  
  
    Le fichier s'ouvre dans l'éditeur de manifeste d'extension.  
  
5. Sur le **actifs** , ajoutez une ligne décrivant le profil :  
  
   -   Cliquez sur **Nouveau**. Définissez les champs dans le **ajouter un nouveau composant** boîte de dialogue comme suit.  
  
   -   Définissez **Type** à `Microsoft.VisualStudio.UmlProfile`  
  
        Cette option ne figure pas dans la liste déroulante. Vous devez entrer ce nom au clavier.  
  
   -   Cliquez sur **fichier sur le système de fichiers** et sélectionnez le nom de votre fichier de profil, par exemple `MyProfile.profile`  
  
6. Générez le projet.  
  
7. **Pour déboguer le profil**, appuyez sur F5.  
  
    Une instance expérimentale de Visual Studio s’ouvre. Dans cette instance, ouvrez un projet de modélisation. Dans l'Explorateur UML, sélectionnez l'élément racine du modèle et, dans la fenêtre Propriétés, sélectionnez votre profil. Ensuite, sélectionnez les éléments à l'intérieur du modèle et définissez les stéréotypes que vous avez définis pour eux.  
  
8. **Pour extraire l’extension VSIX pour le déploiement**  
  
   1.  Dans l’Explorateur Windows, ouvrez le dossier **.\bin\Debug** ou **.\bin\Release** pour trouver la **.vsix** fichier. Il s'agit d'un fichier d'Extension [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Vous pouvez l'installer sur votre ordinateur et l'envoyer à d'autres utilisateurs de Visual Studio.  
  
   2.  Pour installer l'extension  
  
       1.  Double-cliquez sur le fichier `.vsix`. Le Programme d'installation des extensions Visual Studio démarre.  
  
       2.  Redémarrez toutes les instances de Visual Studio qui sont en cours d'exécution.  
  
   Vous pouvez appliquer la procédure suivante pour les petites extensions si vous n'avez pas installé [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
#### <a name="to-define-a-profile-extension-without-using-visual-studio-sdk"></a>Pour définir une extension de profil sans utiliser Visual Studio SDK  
  
1.  Créez un répertoire Windows qui contient les trois fichiers suivants :  
  
    -   *YourProfile* `.profile`  
  
    -   `extension.vsixmanifest`  
  
    -   `[Content_Types].xml` : tapez ce nom comme indiqué ici, avec les crochets  
  
2.  Modifiez `[Content_Types].xml` pour qu'il contienne le texte suivant. Notez qu'il contient une entrée pour chaque extension de nom de fichier.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
      <Default Extension="profile" ContentType="application/octet-stream" />  
      <Default Extension="vsixmanifest" ContentType="text/xml" />  
    </Types>  
    ```  
  
3.  Copiez un fichier `extension.vsixmanifest` existant et modifiez-le avec un éditeur XML. Modifiez les nœuds ID, Name et Content.  
  
    -   Vous trouverez un exemple de `extension.vsixmanifest` dans ce répertoire :  
  
         *lecteur* **: \Program Files\Microsoft Visual Studio [version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles**  
  
    -   Le nœud Content doit ressembler à ceci :  
  
        ```  
        <Content>  
          <CustomExtension Type="Microsoft.VisualStudio.UmlProfile"  
          >YourProfile.Profile</CustomExtension>  
        </Content>  
        ```  
  
4.  Placez les trois fichiers dans un fichier compressé.  
  
     Dans l’Explorateur Windows, sélectionnez les trois fichiers, avec le bouton droit, pointez sur **envoyer vers**, puis cliquez sur **dossier compressé (zippé)**.  
  
5.  Renommez le fichier compressé et remplacez son extension de nom de fichier `.zip` par `.vsix`.  
  
6.  Pour installer le profil sur n'importe quel ordinateur disposant d'une édition appropriée de Visual Studio, double-cliquez sur le fichier `.vsix`.  
  
#### <a name="to-install-a-uml-profile-from-a-visual-studio-extension"></a>Pour installer un profil UML à partir d'une Extension Visual Studio  
  
1.  Double-cliquez sur le fichier `.vsix` dans l'Explorateur Windows ou ouvrez-le dans Visual Studio.  
  
2.  Cliquez sur **installer** dans la boîte de dialogue qui s’affiche.  
  
3.  Pour désinstaller ou temporairement désactiver l’extension, ouvrez **Extensions et mises à jour** à partir de la **outils** menu.  
  
##  <a name="Localized"></a> Comment définir des profils localisés  
 Vous pouvez définir différents profils pour différentes cultures ou langues, et tous les empaqueter dans la même extension. Quand un utilisateur chargera votre extension, ils verra le profil que vous avez défini pour sa culture.  
  
 Vous devez toujours fournir un profil par défaut. Si vous n'avez pas défini de profil pour la culture de l'utilisateur, il verra le profil par défaut.  
  
#### <a name="to-define-a-localized-profile"></a>Pour définir un profil localisé  
  
1.  Créez un profil comme décrit dans les sections précédentes[comment définir un profil](#DefineProfile) et [comment ajouter un profil à une Extension Visual Studio](#AddProfile). Il s'agit du profil par défaut, qui sera utilisé dans les installations pour lesquelles vous ne fournissez pas de profil localisé.  
  
2.  Ajoutez un nouveau répertoire dans le même répertoire que celui où se trouve votre fichier de profil par défaut.  
  
    > [!NOTE]
    >  Si vous générez l'extension à l'aide d'un projet d'Extension Visual Studio, utilisez l'Explorateur de solutions pour ajouter un nouveau dossier au projet.  
  
3.  Modifiez le nom du nouveau répertoire avec le code court ISO de la culture localisée, par exemple `bg` pour le bulgare ou `fr` pour le français. Vous devez utiliser un code de culture neutre, en général deux lettres, et non une culture spécifique telle que `fr-CA`. Pour plus d’informations sur les codes de culture, consultez [méthode CultureInfo.GetCultures](http://go.microsoft.com/fwlink/?LinkId=160782), qui fournit une liste complète des codes de culture.  
  
4.  Ajoutez une copie de votre profil par défaut au nouveau répertoire. Ne modifiez pas son nom de fichier.  
  
     Un exemple [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] dossier d’Extension, avant qu’il est créé ou compressé dans un `.vsix` de fichier, contiendrait les dossiers et fichiers suivants :  
  
     `extension.vsixmanifest`  
  
     `MyProfile.profile`  
  
     `fr\MyProfile.profile`  
  
     `de\MyProfile.profile`  
  
    > [!NOTE]
    >  Vous ne devez pas insérer de référence aux versions localisées des profils dans `extension.vsixmanifest`. Les fichiers de profils copiés doivent avoir le même nom que le profil dans le dossier parent.  
  
5.  Modifiez la nouvelle copie du profil, en traduisant dans la langue cible toutes les parties qui seront visibles par l'utilisateur, telles que les attributs `displayName`.  
  
6.  Vous pouvez créer des profils localisés et des dossiers de culture supplémentaires pour autant de cultures que vous le souhaitez.  
  
7.  Générez l'Extension Visual Studio en créant le projet d'extension ou en compressant tous les fichiers, comme décrit dans les sections précédentes.  
  
##  <a name="Schema"></a> La Structure d’un profil  
 Le fichier XSD pour les profils UML se trouve dans l’exemple suivant : [Définition XSD de stéréotypes et profils](http://go.microsoft.com/fwlink/?LinkID=213811). Pour vous aider à modifier les fichiers de profils, installez le fichier `.xsd` dans :  
  
 **%ProgramFiles%\Microsoft visual Studio [version] \Xml\Schemas**  
  
 Cette section utilise le profil C# comme exemple. La définition de profil complète est visible dans :  
  
 *lecteur* **: \Program Files\Microsoft Visual Studio [version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\CSharp.profile**  
  
 Les premières parties de ce chemin d'accès peuvent différer dans votre installation.  
  
 Pour plus d’informations sur le profil .NET, consultez [stéréotypes Standard pour les modèles UML](../modeling/standard-stereotypes-for-uml-models.md).  
  
### <a name="main-sections-of-the-uml-profile-definition"></a>Principales sections de la définition de profil UML  
 Chaque profil contient ce qui suit :  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<profile dslVersion="1.0.0.0"   
       name="CSharpProfile" displayName="C# Profile"   
       xmlns="http://schemas.microsoft.com/UML2.1.2/ProfileDefinition">  
  <stereotypes>...</stereotypes>  
  <metaclasses>...</metaclasses>  
  <propertyTypes>...</propertyTypes>  
</profile>  
```  
  
> [!NOTE]
>  L'attribut appelé `name` ne doit pas contenir d'espaces ou de signes de ponctuation. L'attribut `displayName`, qui apparaît dans l'interface utilisateur, doit être une chaîne XML valide.  
  
 Chaque profil contient trois sections principales. Dans l'ordre inverse, il s'agit des suivantes :  
  
-   `<propertyTypes>` : liste des types qui sont utilisés pour les propriétés définies dans la section des stéréotypes.  
  
-   `<metaclasses>` : liste des types d'éléments de modèles auxquels s'appliquent les stéréotypes de ce profil, comme IClass, IInterface, IOperation ou IDependency.  
  
-   `<stereotypes>` : définitions des stéréotypes. Chaque définition comprend les noms et les types de propriétés qui sont ajoutés à l'élément de modèle cible.  
  
#### <a name="property-types"></a>Types de propriétés  
 Le `<propertyTypes>` section déclare une liste des types qui sont utilisés pour les propriétés de la `<stereotypes>` section. Il existe deux genres de types de propriétés : externe et énumération.  
  
 Un type externe déclare le nom qualifié complet d'un type .NET standard :  
  
```  
<externalType name="System.String" />  
```  
  
 Un type énumération définit un ensemble de valeurs littérales :  
  
```  
<enumerationType name="PackageVisibility">  
  <enumerationLiterals>  
    <enumerationLiteral name="internal" displayName="internal"  />  
    <enumerationLiteral name="protectedinternal" displayName="protected internal" />  
  </enumerationLiterals>  
</enumerationType>  
```  
  
#### <a name="metaclasses"></a>Métaclasses  
 La section `<metaclasses>` est une liste de types d'éléments de modèles sur lesquels les stéréotypes de ce profil peuvent être définis :  
  
```  
<metaclass   
      name="Microsoft.VisualStudio.Uml.Classes.IClass" />  
<metaclass  
      name="Microsoft.VisualStudio.Uml.Classes.IInterface" />  
<metaclass  
      name="Microsoft.VisualStudio.Uml.Components.IComponent" />  
```  
  
 Pour obtenir la liste complète des types de relations et d’éléments modèle que vous pouvez utiliser comme métaclasses, consultez [Types d’éléments de modèle](#Elements).  
  
#### <a name="stereotype-definition"></a>Définition de stéréotype  
 La section `<stereotypes>` contient une ou plusieurs définitions de stéréotypes :  
  
```  
<stereotype name="CSharpClass" displayName="C# Class"> ...  
```  
  
 Chaque stéréotype répertorie un ou plusieurs types d'éléments de modèles ou de relations auxquels il peut être appliqué. Vous pouvez donner le nom d'un type de base pour inclure tous ses types dérivés. Par exemple, si vous spécifiez `Microsoft.VisualStudio.Uml.Classes.IType`, le stéréotype peut être appliqué à `IClass`, `IInterface`, `IEnumeration` et plusieurs autres types d'éléments.  
  
```  
<metaclasses>  
  <metaclassMoniker name=  
   "/CSharpProfile/Microsoft.VisualStudio.Uml.Classes.IClass" />  
</metaclasses>  
```  
  
 L'attribut `name` de `metaclassMoniker` est un lien vers un élément dans la section `<metaClasses>`.  
  
> [!NOTE]
>  Le nom du moniker doit commencer par `/yourProfileName/`, où `yourProfileName` est défini dans l'attribut `name` du profil (« CSharpProfile » dans cet exemple). Le moniker se termine par le nom de l'une des entrées dans la section des métaclasses.  
  
 Chaque stéréotype peut répertorier zéro, une ou plusieurs propriétés qu'il ajoute à tout élément de modèle auquel il est appliqué. Le `<propertyType>` contient un lien vers un des types qui sont définis dans la `<propertyTypes>` section. Le lien doit être un `<externalTypeMoniker>` pour faire référence à un `<externalType>,` ou un `<enumerationTypeMoniker>` pour faire référence à un `<enumerationType>`. Là encore, le lien commence par le nom de votre profil.  
  
```  
  <properties>  
    <property name="IsStatic"   
            displayName="Is Static" defaultValue="false">  
      <propertyType>  
<externalTypeMoniker   
               name="/CSharpProfile/System.Boolean" />  
      </propertyType>  
    </property>  
    <property name="PackageVisibility"   
              displayName="Package Visibility"  
              defaultValue="internal">  
      <propertyType>  
        <enumerationTypeMoniker   
              name="/CSharpProfile/PackageVisibility"/>  
      </propertyType>  
    </property>  
  </properties>  
</stereotype>  
```  
  
##  <a name="Elements"></a> Types d’éléments de modèle  
 L’ensemble de types pour laquelle vous pouvez définir des stéréotypes est répertorié dans [types d’éléments UML modèle](../modeling/uml-model-element-types.md).  
  
## <a name="troubleshooting"></a>Résolution des problèmes  
 Mes stéréotypes n'apparaissent pas dans mes modèles UML.  
 Vous devez sélectionner votre profil dans un package ou un modèle. Les stéréotypes apparaîtront alors sur les éléments dans le package ou le modèle. Pour plus d’informations, consultez [ajouter des stéréotypes à UML les éléments de modèle](../modeling/add-stereotypes-to-uml-model-elements.md).  
  
 L’erreur suivante s’affiche lorsque j’ouvre un modèle UML : **VS1707 : Impossible de charger les profils suivants, car une erreur de sérialisation s’est produite : MyProfile.profile**  
 1.  Vérifiez que la syntaxe XML de base du fichier .profile est correcte.  
  
2. Vérifiez que le nom de chaque Moniker respecte le format /nom_profil/nom_nœud. nom_profil correspond à la valeur de l'attribut name dans le nœud racine du profil. nom_nœud correspond à la valeur de l'attribut name d'une métaclasse, d'un externalType ou d'un enumerationType.  
  
3. Vérifiez que la syntaxe est décrite ici et comme illustré dans _lecteur_**: \Program Files\Microsoft Visual Studio [version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\\** .  
  
4. Désinstallez l'extension défectueuse. Dans le menu **Outils** , choisissez **Extensions et mises à jour**.  
  
   -   Si l'extension n'apparaît pas, consultez le paragraphe suivant.  
  
5. Régénérez le fichier VSIX et ouvrez-le dans l'Explorateur Windows pour le réinstaller. Redémarrez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
   L’extension n’apparaît pas dans le Gestionnaire d’extensions, mais lorsque vous essayez de réinstaller, le message suivant apparaît : **L’extension est déjà installée dans tous les produits applicables.**  
   1.  Supprimer le fichier d’extension à partir d’un sous-dossier de *LocalAppData*\Microsoft\VisualStudio\\[version] \Extensions\  
  
   -   Pour voir *LocalAppData*, vous devez définir afficher les fichiers et dossiers cachés dans l’onglet Affichage des Options de dossier de l’Explorateur Windows.  
  
   -   *LocalAppData* est en général dans C:\Users\\*nom d’utilisateur*\AppData\Local\  
  
6. Redémarrez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des stéréotypes à des éléments de modèle UML](../modeling/add-stereotypes-to-uml-model-elements.md)   
 [Personnaliser votre modèle avec des profils et stéréotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [Stéréotypes standard pour les modèles UML](../modeling/standard-stereotypes-for-uml-models.md)   
 [Exemple : Couleur des éléments UML par stéréotype](http://go.microsoft.com/fwlink/?LinkID=213841)   
 [Exemple : Définition des stéréotypes et des profils XSD](http://go.microsoft.com/fwlink/?LinkID=213811)
