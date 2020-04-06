---
title: Enregistrement d’un service de langue héritée2 Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d9d13f301f6c04c0f7b14cc8c685f08b072ef84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705888"
---
# <a name="registering-a-legacy-language-service"></a>Inscription d’un service de langage hérité
Les sections suivantes fournissent des listes d’inscriptions [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]au registre pour les différentes options de service linguistique disponibles en .

 Dans la liste suivante des entrées de registre, *VS Reg Root* est égal\\à HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio*X.Y*, où *X.Y* est le numéro de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] version.

## <a name="registry-entries-for-language-service-options"></a>Inscriptions au registre pour les options de service linguistique
 La clé DE nom de\\la*langue* VS Reg *Root*'Languages’Language Services peut contenir les valeurs suivantes.

|Nom|Type|Plage|Description|
|----------|----------|-----------|-----------------|
|(Par défaut)|REG_SZ|*\<>GUID*|GUID du service linguistique.|
|LangResID (LangResID)|REG_DWORD|0x0-0xffff|Identifiant de ressources de chaîne (ResID) pour le nom de texte localisé de la langue.|
|Package|REG_SZ|*\<>GUID*|GUID du VSPackage.|
|ShowCompletion|REG_DWORD|0-1|Précise si les options **d’achèvement de l’énoncé** dans la boîte de dialogue **Options** sont activées.|
|SpectaclesSmartIndent|REG_DWORD|0-1|Précise si l’option de sélection de l’indenting **intelligent** dans la boîte de dialogue **Options** est activée.|
|RequestStockColors (en)|REG_DWORD|0-1|Précise si les couleurs personnalisées ou par défaut sont utilisées pour colorer les mots clés.|
|ShowHotURLs ShowHotURLs|REG_DWORD|0-1|Précise si l’utilisateur peut cliquer sur les URL.|
|Par défaut pour les URL non chaudes|REG_DWORD|0-1|Spécifie le paramètre initial de **l’option de navigation URL Active en un seul clic** dans la boîte de dialogue **Options.**|
|DefaultToInsertSpaces|REG_DWORD|0-1|Précise si le service linguistique a des « espaces d’insertion » comme option d’onglet par défaut.|
|ShowDropdownBarOption|REG_DWORD|0-1|Permet ou désactive l’option **barre de navigation** dans la boîte de dialogue **Options** qui affiche ou cache la barre **de navigation**.|
|Fenêtre à code unique seulement|REG_DWORD|0-1|Permet ou désactive le choix **New Window** dans le menu **Fenêtre** pour un service linguistique.|
|EnableAdvancedMembersOption|REG_DWORD|0-1|Permet ou désactive un réglage de boîte de dialogue **Options** pour **masquer les membres avancés**.|
|Soutien CF_HTML|REG_DWORD|0-1|Précise si l’éditeur permet la copie et le coller des données HTML.|
|EnableLineNumbersOption|REG_DWORD|0-1|Précise si les options **de numéros de ligne** dans la boîte de dialogue **Options** sont activées pour un service linguistique.|
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Précise si les membres avancés tels que les champs privés sont cachés dans les listes d’achèvement.|
|ShowBraceComplétion|REG_DWORD|0-1|Précise si l’option **d’achèvement Brace** dans la boîte de dialogue **Options** est activée.|

### <a name="example"></a>Exemple

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
        LangResID             = reg_dword:0x00000000
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}
        ShowCompletion        = reg_dword:0x00000001
        ShowSmartIndent       = reg_dword:0x00000001
        ShowDropdownBarOption = reg_dword:0x00000001
```

## <a name="registry-entries-for-debugger-languages-options"></a>Inscriptions au registre pour les options de langues de débbugger
 Le NOM*de la langue*VS Reg *Root*'Languages’Language Services\\'Debugger Languages\\*GUID*' ' peut inclure les valeurs suivantes.

|Nom|Type|Plage|Description|
|----------|----------|-----------|-----------------|
|(Par défaut)|REG_SZ|text|La valeur par défaut peut être utilisée pour documenter le nom de la langue. Le nom de cette clé est un GUID d’un * \< *évaluateur d’expression qui a une entrée correspondante dans VS Reg Root>'AD7Metrics’Expression Evaluator.|

### <a name="example"></a>Exemple

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        Debugger Languages\
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\
            (Default) = reg_sz:C++
```

## <a name="registry-entries-for-editor-tools-options"></a>Inscriptions au registre pour les options d’outils de l’éditeur
 Vous pouvez ajouter des clés de registre sous la clé EditorToolsOptions pour les pages de propriété et les nœuds de propriété. Ces clés et leurs valeurs identifient les pages de propriété dans la boîte de dialogue **Options** (sur le menu **Tools)** qui sont utilisées pour configurer le service linguistique. Dans l’exemple suivant, *Page Name* est le nom d’une page de propriété, et *Node Name* est le nom d’un nœud dans l’arbre sur la boîte de dialogue **Options.** L’entrée de la page et l’entrée du nœud doivent être spécifiées séparément.

|Nom|Type|Plage|Description|
|----------|----------|-----------|-----------------|
|(Par défaut)|REG_SZ|ResID (ResID)|Le nom d’affichage localisé de cette page d’option. Le nom peut être le`nnn`texte `nnn` littéral, ou , où est une pièce d’identité de ressource de chaîne dans le satellite DLL de la VSPackage spécifié.|
|Package|REG_SZ|*GUID*|Le GUID du VSPackage qui implémente cette page d’options.|
|Page|REG_SZ|*GUID*|Le GUID de la page de propriété à <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> demander à partir de la VSPackage en appelant la méthode. Si cette inscription au registre n’est pas présente, la clé du registre décrit un nœud et non une page.|

### <a name="example"></a>Exemple

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      CSharp\
        EditorToolsOptions\
          Formatting\
            (Default) = reg_sz:#242
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
            General\
              (Default) = reg_sz:#255
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}
            Indentation\
              (Default) = reg_sz:#250
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}
            Newlines\
              (Default) = reg_sz:#253
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}
```

## <a name="registry-entries-for-file-name-extension-options"></a>Inscriptions au registre pour les options d’extension du nom de fichier
 L’entrée pour l’extension du fichier devrait inclure la période de tête, par exemple ".myext".

|Nom|Type|Plage|Description|
|----------|----------|-----------|-----------------|
|(Par défaut)|REG_SZ|*GUID*|Service GUID pour le service de langue par défaut pour ce type d’extension de nom de fichier.|

### <a name="example"></a>Exemple

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>Inscriptions au registre des options d’éditeur
 La clé *VS Reg Root*'Editors peut contenir les valeurs suivantes :

|Nom|Type|Plage|Description|
|----------|----------|-----------|-----------------|
|(Par défaut)|REG_SZ|""|Inutilisé; vous pouvez mettre votre nom ici pour la documentation.|
|DefaultToolboxTab|REG_SZ|""|Nom de l’onglet boîte à outils pour faire défaut lorsque l’éditeur est actif.|
|DisplayName|REG_SZ|ResID (ResID)|Nom à afficher dans la boîte de dialogue **Open With.** Le nom est l’ID de ressource de chaîne ou un nom dans le format standard.|
|ExcluDefTextEditor|REG_DWORD|0-1|Utilisé pour **l’Open With** menu command. Si vous ne souhaitez pas inscrire l’éditeur de texte par défaut dans la liste des éditeurs disponibles pour un type de fichier spécifique, définissez cette valeur à 1.|
|LinkedEditorGUID (en)|REG_SZ|*\<>GUID*|Utilisé pour tout service linguistique qui peut ouvrir un fichier avec support de page de code. Par exemple, lorsque vous ouvrez un fichier .txt en utilisant la commande **Open With,** des options sont prévues pour l’utilisation de l’éditeur de code source avec et sans codage.<br /><br /> Le GUID spécifié au nom du sous-clé est pour l’usine d’éditeur de page de code; le GUID lié spécifié dans cette entrée de registre spécifique est pour l’usine d’éditeur régulière. Le but de cette entrée est que si l’IDE n’ouvre pas un fichier en utilisant l’éditeur par défaut, l’IDE va essayer d’utiliser le prochain éditeur dans la liste. Ce prochain éditeur ne devrait pas être l’usine d’éditeur de page de code parce que cette usine d’éditeur est fondamentalement la même que l’usine de rédacteur qui a échoué.|
|Package|REG_SZ|*\<>GUID*|VSPackage GUID pour resID du nom d’affichage.|

### <a name="example"></a>Exemple

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      (Default)            = reg_sz:Html Editor with Encoding
      DefaultToolboxTab    = reg_sz:HTML
      DisplayName          = reg_sz:#20101
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}
```

## <a name="registry-entries-for-logical-view-options"></a>Inscriptions au registre pour les options de vue logique
 La *clé DE l’éditeur DE VS Reg Root,*\\QUI *>*'LogicalViews' peut contenir les valeurs suivantes.

|Nom|Type|Plage|Description|
|----------|----------|-----------|-----------------|
|(Par défaut)|REG_SZ||Inutilisé.|
|*\<>GUID*|REG_SZ|""|Clé des points de vue logiques pris en charge. Vous pouvez en avoir autant que vous en avez besoin. Le nom de l’entrée du registre est ce qui est important, pas la valeur, qui est toujours une chaîne vide.|

### <a name="example"></a>Exemple

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      LogicalViews\
       (Default) = reg_sz:
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
```

## <a name="registry-entries-for-editor-extension-options"></a>Inscriptions au registre pour les options d’extension de l’éditeur
 La clé *DE l’éditeur DE VS Reg Root*,\\*l’éditeur GUID*et les extensions, peut contenir les valeurs suivantes. L’extension du nom de fichier n’inclut pas la période de tête.

|Nom|Type|Plage|Description|
|----------|----------|-----------|-----------------|
|(Par défaut)|REG_SZ||Inutilisé.|
|*\<ext>*|REG_DWORD|0-0xffffffffffffff|Priorité relative des extensions. Si deux langues ou plus partagent la même extension, la langue prioritaire est choisie.|

 En outre, la sélection par défaut de l’utilisateur actuel pour un éditeur est\\stockée dans HKEY_Current_User-Software-Microsoft-VisualStudio*X.Y*'Default Editors\\*ext*. Le GUID du service linguistique sélectionné est dans l’entrée personnalisée. Cela prime pour l’utilisateur actuel.

### <a name="example"></a>Exemple

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      Extensions\
       (Default) = reg_sz:
       *         = reg_dword:0x00000018
       html      = reg_dword:0x00000027
       shtm      = reg_dword:0x00000027
       shtml     = reg_dword:0x00000027
```

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Inscriptions au registre pour les options de services linguistiques-cadres de forfait gérées
 Les inscriptions suivantes au registre sont spécifiques aux cours de service linguistique du cadre de forfait géré (MPF). Ces entrées de registre indiquent le soutien dans le service linguistique pour diverses fonctionnalités IntelliSense et pour d’autres fonctionnalités d’édition avancées.

 Ces inscriptions au registre <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sont consultées par l’intermédiaire de la classe.

|Nom|Type|Plage|Description|
|----------|----------|-----------|-----------------|
|CodeSense (en anglais)|REG_DWORD|0-1|Soutien aux opérations d’IntelliSense.|
|MatchBraces (en anglais)|REG_DWORD|0-1|Soutien pour les paires de langage assorties telles que les accolades, les parenthèses et les parenthèses.|
|Info express|REG_DWORD|0-1|Soutien à l’opération IntelliSense Quick Info.|
|ShowMatchingBrace|REG_DWORD|0-1|Soutien pour l’affichage de la paire de langue assortie dans la barre d’état.|
|MatchBracesAtCaret|REG_DWORD|0-1|Soutien pour l’affichage des paires de langage assorties, généralement en mettant en évidence les deux éléments.|
|MaxErrorMessages|REG_DWORD|0-n|Le nombre maximum d’erreurs qui peuvent être affichées dans la fenêtre **de la liste d’erreurs.**|
|CodeSenseDelay (en anglais seulement)|REG_DWORD|0-n|Le nombre de millisecondes à retarder avant d’initier tout analyse de fond pour une opération IntelliSense.|
|EnableAsyncCompletion|REG_DWORD|0-1|Soutien à l’analyse de fond.|
|EnableCommenting (en)|REG_DWORD|0-1|La prise en charge pour commenter certains blocs de texte, et implique également la prise en charge de l’inconstituation du texte sélectionné.|
|ActiveFormatSelection|REG_DWORD|0-1|Prise en charge pour le formatage du texte tel que l’auto-indentation ou l’ajustement de la position des accolades.|
|AutoOutlining|REG_DWORD|0-1|Soutien à l’énoncé (régions qui peuvent s’effondrer).|
|MaxRegions (en)|REG_DWORD|0-n|Le nombre maximum de régions cachées par fichier.|

```
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      XML\
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}
        MatchBraces           = reg_dword:0x00000001
        QuickInfo             = reg_dword:0x00000001
        ShowMatchingBrace     = reg_dword:0x00000001
        MatchBracesAtCaret    = reg_dword:0x00000000
        MaxErrorMessages      = reg_dword:0x00000064
        CodeSenseDelay        = reg_dword:0x000001f4
        MaxRegions            = reg_dword:0x0000000a
```

## <a name="see-also"></a>Voir aussi
- [Développement d’un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)
