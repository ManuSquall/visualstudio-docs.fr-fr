---
title: Techniques de débogage MFC | Microsoft Docs
description: 'Découvrez les techniques de débogage des programmes MFC, notamment : points d’arrêt codés, traçage, détection des fuites de mémoire, images mémoire de l’objet et réduction de la taille du programme.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- AfxEnableMemoryTracking
- CMemoryState
- delayFreeMemDF
- checkAlwaysMemDF
- vs.debug.mfc
- vs.debug.objects.dump
- vs.debug.memory.dump
- allocMemDF
- afxMemDF
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC]
ms.assetid: b154fc31-5e90-4734-8cbd-58dd9fe1f750
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5cf00191aff408b1133c281e10eea17e3a923215
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975119"
---
# <a name="mfc-debugging-techniques"></a>Techniques de débogage MFC
Si vous déboguez un programme MFC, les techniques de débogage suivantes peuvent vous être utiles.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Dans cette rubrique
[AfxDebugBreak](#BKMK_AfxDebugBreak)

[Macro TRACE](#BKMK_The_TRACE_macro)

[Détection des fuites de mémoire dans les MFC](#BKMK_Memory_leak_detection_in_MFC)

- [Suivi des allocations de mémoire](#BKMK_Tracking_memory_allocations)

- [Activation des diagnostics de la mémoire](#BKMK_Enabling_memory_diagnostics)

- [Captures instantanées de la mémoire](#BKMK_Taking_memory_snapshots)

- [Affichage des statistiques de la mémoire](#BKMK_Viewing_memory_statistics)

- [Création de dumps d'objets](#BKMK_Taking_object_dumps)

  - [Interprétation des vidages de mémoire](#BKMK_Interpreting_memory_dumps)

  - [Personnalisation des dumps d'objets](#BKMK_Customizing_object_dumps)

  - [Réduction de la taille d'une version Debug MFC](#BKMK_Reducing_the_size_of_an_MFC_Debug_build)

  - [Génération d'une application MFC avec les informations de débogage pour les modules sélectionnés](#BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules)

## <a name="afxdebugbreak"></a><a name="BKMK_AfxDebugBreak"></a> Spéciale AfxDebugBreak,
Les MFC fournissent une fonction spéciale, [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) , pour encoder de manière irréversible les points d'arrêt dans le code source :

```cpp
AfxDebugBreak( );
```

Sur les plateformes Intel, `AfxDebugBreak` produit le code suivant, qui marque une interruption dans le code source, plutôt que dans le code de noyau :

```cpp
_asm int 3
```

Sur les autres plateformes, `AfxDebugBreak` appelle simplement `DebugBreak`.

Veillez à supprimer les instructions `AfxDebugBreak` lorsque vous créez une version Release ou utilisez `#ifdef _DEBUG` pour les délimiter.

[Dans cette rubrique](#BKMK_In_this_topic)

## <a name="the-trace-macro"></a><a name="BKMK_The_TRACE_macro"></a> La macro TRACE
Pour afficher les messages de votre programme dans la [fenêtre Sortie](../ide/reference/output-window.md)du débogueur, vous pouvez utiliser la macro [ATLTRACE](/previous-versions/6xkxyz08(v=vs.140)) ou la macro MFC [TRACE](/previous-versions/6w95a4ha(v=vs.140)) . De même que les [assertions](../debugger/c-cpp-assertions.md), les macros trace sont actives uniquement dans la version Debug de votre programme et disparaissent après la compilation dans la version Release.

Les exemples suivants présentent certaines utilisations possibles de la macro **TRACE** . À l'instar de `printf`, la macro **TRACE** peut gérer un certain nombre d'arguments.

```cpp
int x = 1;
int y = 16;
float z = 32.0;
TRACE( "This is a TRACE statement\n" );

TRACE( "The value of x is %d\n", x );

TRACE( "x = %d and y = %d\n", x, y );

TRACE( "x = %d and y = %x and z = %f\n", x, y, z );
```

La macro TRACE gère correctement les paramètres char \* et wchar_t \* . Les exemples suivants illustrent l'utilisation de la macro TRACE avec différents types de paramètres de chaînes.

```cpp
TRACE( "This is a test of the TRACE macro that uses an ANSI string: %s %d\n", "The number is:", 2);

TRACE( L"This is a test of the TRACE macro that uses a UNICODE string: %s %d\n", L"The number is:", 2);

TRACE( _T("This is a test of the TRACE macro that uses a TCHAR string: %s %d\n"), _T("The number is:"), 2);
```

Pour plus d'informations sur la macro **TRACE** , consultez [Services de diagnostic](/cpp/mfc/reference/diagnostic-services).

[Dans cette rubrique](#BKMK_In_this_topic)

## <a name="detecting-memory-leaks-in-mfc"></a><a name="BKMK_Memory_leak_detection_in_MFC"></a> Détection des fuites de mémoire dans les applications MFC
Les MFC fournissent des classes et des fonctions pour détecter la mémoire qui est allouée, mais jamais désallouée.

### <a name="tracking-memory-allocations"></a><a name="BKMK_Tracking_memory_allocations"></a> Suivi des allocations de mémoire
Dans les MFC, vous pouvez utiliser la macro [DEBUG_NEW](/previous-versions/tz7sxz99(v=vs.140)) à la place de l'opérateur **new** pour faciliter la localisation des fuites de mémoire. Dans la version Debug de votre programme, `DEBUG_NEW` assure le suivi du nom du fichier et du numéro de ligne pour chaque objet alloué. Lorsque vous compilez une version Release de votre programme, `DEBUG_NEW` est traduit en une opération **new** simple sans les informations de nom de fichier et de numéro de ligne. Ainsi, la vitesse n'est pas pénalisée dans la version Release de votre programme.

Si vous voulez éviter de réécrire le programme entier pour utiliser `DEBUG_NEW` à la place de **new**, vous pouvez définir la macro suivante dans vos fichiers sources :

```cpp
#define new DEBUG_NEW
```

Lorsque vous faites un [dump d'objets](#BKMK_Taking_object_dumps), chaque objet alloué avec `DEBUG_NEW` affiche le fichier et le numéro de ligne où il a été alloué, ce qui vous permet de localiser l'origine des fuites de mémoire.

La version Debug de l'infrastructure MFC utilise automatiquement `DEBUG_NEW` , contrairement à votre code. Si vous voulez bénéficier de `DEBUG_NEW`, vous devez utiliser `DEBUG_NEW` explicitement ou **#define new** comme indiqué plus haut.

[Dans cette rubrique](#BKMK_In_this_topic)

### <a name="enabling-memory-diagnostics"></a><a name="BKMK_Enabling_memory_diagnostics"></a> Activation des diagnostics de la mémoire
Avant d'utiliser les fonctions de diagnostic de la mémoire, vous devez activer le traçage de diagnostic.

**Pour activer ou désactiver les diagnostics de la mémoire**

- Appelez la fonction globale [AfxEnableMemoryTracking](/previous-versions/hzsxb6e8(v=vs.140)) pour activer ou désactiver l'allocateur de mémoire de diagnostic. Étant donné que les diagnostics de la mémoire se trouvent par défaut dans la bibliothèque de débogage, vous utiliserez normalement cette fonction pour les désactiver provisoirement, ce qui vous permettra d'augmenter la vitesse d'exécution du programme et de réduire la sortie des diagnostics.

  **Pour sélectionner des fonctionnalités de diagnostic de la mémoire spécifiques avec afxMemDF**

- Si vous voulez contrôler plus précisément les fonctionnalités de diagnostic de la mémoire, vous pouvez les activer et les désactiver individuellement, de façon sélective, en définissant la valeur de la variable globale MFC [afxMemDF](/previous-versions/ahe4a83t(v=vs.140)). Cette variable peut prendre les valeurs suivantes, comme spécifié par le type énuméré **afxMemDF**:

  |Valeur|Description|
  |-----------|-----------------|
  |**allocMemDF**|Activer l'allocateur de mémoire de diagnostic (par défaut).|
  |**delayFreeMemDF**|Différer la libération de la mémoire lors des appels à `delete` ou `free` jusqu'à ce que le programme s'arrête. Votre programme allouera alors la quantité maximale de mémoire possible.|
  |**checkAlwaysMemDF**|Appeler [AfxCheckMemory](/cpp/mfc/reference/diagnostic-services#afxcheckmemory) chaque fois que la mémoire est allouée ou libérée.|

  Vous pouvez combiner ces valeurs en effectuant une opération OR logique, comme indiqué ci-après :

  ```C++
  afxMemDF = allocMemDF | delayFreeMemDF | checkAlwaysMemDF;
  ```

  [Dans cette rubrique](#BKMK_In_this_topic)

### <a name="taking-memory-snapshots"></a><a name="BKMK_Taking_memory_snapshots"></a> Captures instantanées de la mémoire

1. Créez un objet [CMemoryState](/previous-versions/visualstudio/visual-studio-2010/2ads32e2(v=vs.100)) et appelez la fonction membre [CMemoryState::Checkpoint](/cpp/mfc/reference/cmemorystate-structure#checkpoint) . Le premier instantané de la mémoire est alors créé.

2. Une fois que le programme a effectué ses opérations d'allocation et de libération de mémoire, créez un autre objet `CMemoryState` et appelez `Checkpoint` pour cet objet. Vous obtenez ainsi un deuxième instantané de l'utilisation de la mémoire.

3. Créez un troisième objet `CMemoryState` et appelez sa fonction membre [CMemoryState::Difference](/cpp/mfc/reference/cmemorystate-structure#difference) en fournissant les deux précédents objets `CMemoryState` comme arguments. S'il existe une différence entre les deux états de la mémoire, la fonction `Difference` retourne une valeur autre que zéro. Cela indique que certains blocs de mémoire n'ont pas été libérés.

    L'exemple suivant présente l'aspect du code :

    ```cpp
    // Declare the variables needed
    #ifdef _DEBUG
        CMemoryState oldMemState, newMemState, diffMemState;
        oldMemState.Checkpoint();
    #endif

        // Do your memory allocations and deallocations.
        CString s("This is a frame variable");
        // The next object is a heap object.
        CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );

    #ifdef _DEBUG
        newMemState.Checkpoint();
        if( diffMemState.Difference( oldMemState, newMemState ) )
        {
            TRACE( "Memory leaked!\n" );
        }
    #endif
    ```

    Notez que les instructions de vérification de la mémoire sont placées entre des blocs **#ifdef _DEBUG/#endif** afin qu’ils soient compilés uniquement dans les versions Debug de votre programme.

    Maintenant que vous connaissez l’existence d’une fuite de mémoire, vous pouvez utiliser une autre fonction membre, [CMemoryState::DumpStatistics](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) , qui vous aidera à la localiser.

    [Dans cette rubrique](#BKMK_In_this_topic)

### <a name="viewing-memory-statistics"></a><a name="BKMK_Viewing_memory_statistics"></a> Affichage des statistiques de la mémoire
La fonction [CMemoryState::Difference](/cpp/mfc/reference/cmemorystate-structure#difference) examine deux objets d’état de mémoire et détecte les objets qui n’ont pas été libérés du tas entre les états de début et de fin. Une fois que vous avez effectué des instantanés de la mémoire et que vous les avez comparés à l’aide de `CMemoryState::Difference`, vous pouvez appeler [CMemoryState::DumpStatistics](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) pour obtenir des informations sur les objets qui n’ont pas été libérés.

Prenons l’exemple suivant :

```cpp
if( diffMemState.Difference( oldMemState, newMemState ) )
{
    TRACE( "Memory leaked!\n" );
    diffMemState.DumpStatistics();
}
```

Un exemple de dump de cet exemple aura l'aspect suivant :

```cpp
0 bytes in 0 Free Blocks
22 bytes in 1 Object Blocks
45 bytes in 4 Non-Object Blocks
Largest number used: 67 bytes
Total allocations: 67 bytes
```

Les blocs libres sont des blocs dont la fin d'allocation est différée si `afxMemDF` a la valeur `delayFreeMemDF`.

Les blocs Object ordinaires, affichés sur la deuxième ligne, restent alloués sur le tas.

Les blocs non objet incluent les tableaux et les structures alloués avec `new`. Dans le cas présent, quatre blocs non objet ont été alloués sur le tas, mais pas libérés.

`Largest number used` donne la mémoire maximale utilisée par le programme à un moment quelconque.

`Total allocations` donne la quantité totale de mémoire utilisée par le programme.

[Dans cette rubrique](#BKMK_In_this_topic)

### <a name="taking-object-dumps"></a><a name="BKMK_Taking_object_dumps"></a> Exécution de dumps d’objets
Dans un programme MFC, vous pouvez utiliser [CMemoryState ::D umpallobjectssince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) pour faire un dump d’une description de tous les objets sur le tas qui n’ont pas été libérés. `DumpAllObjectsSince` permet de faire un dump de tous les objets alloués depuis le dernier [CMemoryState::Checkpoint](/cpp/mfc/reference/cmemorystate-structure#checkpoint). Si aucun appel à `Checkpoint` n'a eu lieu, `DumpAllObjectsSince` fait un dump de tous les objets et non-objets actuellement en mémoire.

> [!NOTE]
> Avant de pouvoir utiliser le dump d'objets MFC, vous devez [activer le traçage de diagnostic](#BKMK_Enabling_memory_diagnostics).

> [!NOTE]
> MFC fait automatiquement un dump de tous les objets qui ont été perdus lorsque votre programme s'arrête ; il est donc inutile de créer du code pour faire un dump des objets en ce point.

Le code suivant recherche une fuite de mémoire en comparant deux états de mémoire et fait un dump de tous les objets si une fuite est détectée.

```cpp
if( diffMemState.Difference( oldMemState, newMemState ) )
{
    TRACE( "Memory leaked!\n" );
    diffMemState.DumpAllObjectsSince();
}
```

Le contenu du dump a l'aspect suivant :

```cmd
Dumping objects ->

{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215

{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long
```

Les valeurs numériques entre parenthèses au début de la plupart des lignes spécifient l'ordre dans lequel les objets ont été alloués. Le dernier objet alloué, auquel correspond le numéro le plus élevé, apparaît en au début du dump.

Pour obtenir la quantité d'informations maximale d'un dump d'objets, vous pouvez remplacer la fonction membre `Dump` de n'importe quel objet dérivé de `CObject`pour personnaliser le dump d'objets.

Vous avez la possibilité de définir un point d'arrêt sur une allocation de mémoire particulière en affectant à la variable globale `_afxBreakAlloc` la valeur numérique affichée entre parenthèses. Si vous réexécutez le programme, le débogueur arrêtera l'exécution lorsque cette allocation aura lieu. Vous pourrez alors examiner la pile des appels pour savoir comment votre programme est parvenu jusqu'à ce point.

La bibliothèque Runtime C possède une fonction similaire, [_CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc), que vous pouvez utiliser pour les allocations Runtime C.

[Dans cette rubrique](#BKMK_In_this_topic)

#### <a name="interpreting-memory-dumps"></a><a name="BKMK_Interpreting_memory_dumps"></a> Interprétation des vidages mémoire
Examinons ce dump d'objets plus en détail :

```cmd
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215

{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long
```

Le programme qui a généré ce dump n'avait que deux allocations explicites : une sur la pile, l'autre sur le tas :

```cpp
// Do your memory allocations and deallocations.
CString s("This is a frame variable");
// The next object is a heap object.
CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
```

Le constructeur `CPerson` prend trois arguments qui correspondent à des pointeurs vers `char`, utilisés pour initialiser les variables membres `CString` . Dans le dump mémoire, vous pouvez voir l'objet `CPerson` avec trois blocs non-objets (3, 4 et 5). Ces derniers contiennent les caractères pour les variables membres `CString` et ne seront pas supprimés lorsque le destructeur d'objet `CPerson` sera appelé.

Le bloc numéro 2 est l'objet `CPerson` lui-même. `$51A4` représente l'adresse du bloc, laquelle est suivie du contenu de l'objet, qui a été sorti par `CPerson`::`Dump` lorsque ce dernier a été appelé par [DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince).

Vous pouvez deviner que le bloc numéro 1 est associé à la variable frame `CString` en raison de son numéro de séquence et de sa taille, qui correspond au nombre de caractères dans la `CString` variable. Les variables allouées sur le frame sont automatiquement désallouées lorsque le frame est hors de portée.

**Variables frame**

En général, vous n'avez pas à vous soucier des objets de tas associés à des variables frame, car ils sont automatiquement désalloués lorsque celles-ci sont hors de portée. Afin d'éviter tout encombrement dans les dumps des diagnostics de la mémoire, vous devez positionner vos appels à `Checkpoint` de telle sorte qu'ils se trouvent hors de la portée des variables frame. Par exemple, placez des parenthèses de portée autour du code d'allocation, comme indiqué ci-après :

```cpp
oldMemState.Checkpoint();
{
    // Do your memory allocations and deallocations ...
    CString s("This is a frame variable");
    // The next object is a heap object.
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
}
newMemState.Checkpoint();
```

Une fois la portée mise entre parenthèses, le dump mémoire, pour cet exemple, se présente de la façon suivante :

```cmd
Dumping objects ->

{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215
```

**Allocations non-objets**

Comme vous pouvez le remarquer, certaines allocations sont des objets (tels que `CPerson`), tandis que d’autres sont des allocations non-objets. Les « allocations non-objets » sont des allocations pour des objets qui ne dérivent pas de `CObject` ou des allocations de types C primitifs, tels que `char`, `int` ou `long`. Si la classe dérivée <strong>CObject -</strong>alloue de l'espace supplémentaire (pour les mémoires tampons internes, par exemple), ces objets afficheront à la fois des allocations objets et non-objets.

**Prévention des fuites de mémoire**

Notez que, dans le code ci-dessus, le bloc de mémoire associé à la variable frame `CString` a été désalloué automatiquement et n'apparaît pas comme une fuite de mémoire. La désallocation automatique associée aux règles de portée se charge de la plupart des fuites de mémoire associées aux variables frame.

Dans le cas des objets alloués sur le tas, cependant, vous devez supprimer l'objet de façon explicite pour éviter une fuite de mémoire. Pour nettoyer la dernière fuite de mémoire dans l'exemple précédent, supprimez l'objet `CPerson` alloué sur le tas, comme indiqué ci-après :

```cpp
{
    // Do your memory allocations and deallocations.
    CString s("This is a frame variable");
    // The next object is a heap object.
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
    delete p;
}
```

[Dans cette rubrique](#BKMK_In_this_topic)

#### <a name="customizing-object-dumps"></a><a name="BKMK_Customizing_object_dumps"></a> Personnalisation des dumps d’objets
Lorsque vous dérivez une classe de [CObject](/cpp/mfc/reference/cobject-class), vous pouvez substituer la fonction membre `Dump` pour fournir des informations supplémentaires lorsque vous utilisez [DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) pour faire un dump des objets dans la [fenêtre Sortie](../ide/reference/output-window.md).

La fonction `Dump` écrit une représentation textuelle des variables de membre de l'objet dans un contexte de dump ([CDumpContext](/cpp/mfc/reference/cdumpcontext-class)). Le contexte de dump est similaire à un flux d'E/S. Vous pouvez utiliser l’opérateur Append ( **<<** ) pour envoyer des données à un `CDumpContext` .

Lorsque vous substituez la fonction `Dump` , vous devez d'abord appeler la version classe de base de la fonction `Dump` pour faire un dump du contenu de l'objet de classe de base. Sortez ensuite une description texte et une valeur pour chaque variable de membre de votre classe dérivée.

La déclaration de la fonction `Dump` se présente de la façon suivante :

```cpp
class CPerson : public CObject
{
public:
#ifdef _DEBUG
    virtual void Dump( CDumpContext& dc ) const;
#endif

    CString m_firstName;
    CString m_lastName;
    // And so on...
};
```

Dans la mesure où le dump d'objets n'a de sens que dans le cadre du débogage de votre programme, la déclaration de la fonction `Dump` est mise entre parenthèses avec un bloc **#ifdef _DEBUG / #endif** .

Dans l'exemple suivant, la fonction `Dump` appelle d'abord la fonction `Dump` pour sa classe de base. Elle écrit ensuite une brève description de chaque variable de membre avec la valeur du membre dans le flux du diagnostic.

```cpp
#ifdef _DEBUG
void CPerson::Dump( CDumpContext& dc ) const
{
    // Call the base class function first.
    CObject::Dump( dc );

    // Now do the stuff for our specific class.
    dc << "last name: " << m_lastName << "\n"
        << "first name: " << m_firstName << "\n";
}
#endif
```

Vous devez fournir un argument `CDumpContext` pour spécifier la destination de la sortie du dump. La version Debug des MFC fournit un objet `CDumpContext` prédéfini, nommé `afxDump` , qui envoie la sortie au débogueur.

```cpp
CPerson* pMyPerson = new CPerson;
// Set some fields of the CPerson object.
//...
// Now dump the contents.
#ifdef _DEBUG
pMyPerson->Dump( afxDump );
#endif
```

[Dans cette rubrique](#BKMK_In_this_topic)

## <a name="reducing-the-size-of-an-mfc-debug-build"></a><a name="BKMK_Reducing_the_size_of_an_MFC_Debug_build"></a> Réduction de la taille d’une version Debug MFC
Les informations de débogage pour une application MFC importante peuvent occuper beaucoup d'espace disque. Vous pouvez utiliser une de ces procédures pour réduire la taille :

1. Régénérez les bibliothèques MFC à l’aide de l’option [/Z7,/Zi,/ZI (format des informations de débogage)](/cpp/build/reference/z7-zi-zi-debug-information-format) au lieu de **/Z7**. Ces options génèrent un seul fichier de base de données de programme (PDB), qui contient les informations de débogage pour la bibliothèque entière, ce qui permet de réduire la redondance et d'économiser de l'espace.

2. Régénérez les bibliothèques MFC sans informations de débogage (pas d’option [/Z7,/Zi,/ZI (format des informations de débogage)](/cpp/build/reference/z7-zi-zi-debug-information-format) ). Dans ce cas, l'absence d'informations de débogage vous empêchera d'utiliser la plupart des fonctions de débogage dans le code des bibliothèques MFC, mais étant donné que celles-ci sont déjà déboguées minutieusement, cela n'est pas forcément un problème.

3. Générez votre propre application avec les informations de débogage uniquement pour les modules sélectionnés comme décrit ci-dessous.

    [Dans cette rubrique](#BKMK_In_this_topic)

### <a name="building-an-mfc-app-with-debug-information-for-selected-modules"></a><a name="BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules"></a> Génération d’une application MFC avec les informations de débogage pour les modules sélectionnés
La génération de modules sélectionnés avec les bibliothèques de débogage MFC vous permet d'utiliser le pas à pas et les autres fonctions de débogage dans ces modules. Cette procédure utilise à la fois les configurations Debug et Release du projet, nécessitant ainsi les modifications décrites dans les étapes suivantes (et en faisant également une « régénération totale » nécessaire lorsqu’une version release complète est requise).

1. Dans l’Explorateur de solutions, sélectionnez le projet.

2. Dans le menu **Affichage** , sélectionnez **Pages de propriétés**.

3. Vous commencerez par créer une nouvelle configuration de projet.

   1. Dans la boîte de dialogue **\<Project> pages de propriétés** , cliquez sur le bouton **Configuration Manager** .

   2. Dans la [boîte de dialogue Gestionnaire de configurations](/previous-versions/visualstudio/visual-studio-2010/t1hy4dhz(v=vs.100)), localisez votre projet à l'intérieur de la grille. Dans la colonne **configuration** , sélectionnez **\<New...>** .

   3. Dans la [boîte de dialogue Nouvelle configuration de projet](/previous-versions/visualstudio/visual-studio-2010/0eh8w4cf(v=vs.100)), tapez un nom pour votre nouvelle configuration (par exemple, « Débogage partiel ») dans la zone **Nom de la configuration de projet** .

   4. Dans la liste **Copier les paramètres à partir de** , cliquez sur **Release**.

   5. Cliquez sur **OK** pour fermer la boîte de dialogue **nouvelle configuration de projet** .

   6. Fermez la boîte de dialogue **Gestionnaire de configurations** .

4. Vous définirez ensuite les options pour l'ensemble du projet.

   1. Dans la boîte de dialogue **Pages de propriétés** , sous le dossier **Propriétés de configuration** , sélectionnez la catégorie **Général** .

   2. Dans la grille des paramètres du projet, développez **Paramètres par défaut du projet** (si nécessaire).

   3. Sous **Paramètres par défaut du projet**, recherchez **Utilisation des MFC**. Le paramètre en cours apparaît dans la colonne de droite de la grille. Cliquez sur le paramètre en cours et remplacez-le par **Utiliser les MFC dans une bibliothèque statique**.

   4. Dans le volet gauche de la boîte de dialogue **Pages de propriétés** , ouvrez le dossier **C/C++** et sélectionnez **Préprocesseur**. Dans la grille des propriétés, recherchez **Définitions de préprocesseur** et remplacez « NDEBUG » par « _DEBUG ».

   5. Dans le volet gauche de la boîte de dialogue **Pages de propriétés** , ouvrez le dossier **Éditeur de liens** et sélectionnez **Entrée** Category. Dans la grille des propriétés, recherchez **Dépendances supplémentaires**. Dans le paramètre **Dépendances supplémentaires** , tapez « NAFXCWD.LIB » et « LIBCMT ».

   6. Cliquez sur **OK** pour enregistrer les nouvelles options de génération et fermer la boîte de dialogue **Pages de propriétés** .

5. Dans le menu **Générer** , cliquez sur **Régénérer**. Cela permet de supprimer les informations de débogage de vos modules, sans affecter la bibliothèque MFC.

6. Vous devez à présent ajouter de nouveau les informations de débogage aux modules sélectionnés dans votre application. N'oubliez pas que vous ne pouvez définir des points d'arrêt et exécuter d'autres fonctions de débogage que dans les modules compilés avec les informations de débogage. Pour chaque fichier projet dans lequel vous voulez inclure les informations de débogage, procédez de la façon suivante :

   1. Dans l'Explorateur de solutions, ouvrez le dossier **Fichiers sources** situé sous votre projet.

   2. Sélectionnez le fichier pour lequel vous voulez définir les informations de débogage.

   3. Dans le menu **Affichage** , sélectionnez **Pages de propriétés**.

   4. Dans la boîte de dialogue **Pages de propriétés** , sous le dossier **Configuration Settings** , ouvrez le dossier **C/C++** , puis sélectionnez la catégorie **Général** .

   5. Dans la grille des propriétés, recherchez **Format des informations de débogage.**

   6. Cliquez sur les paramètres de **Format des informations de débogage** et sélectionnez l'option voulue (généralement **/ZI**) pour les informations de débogage.

   7. Si vous utilisez une application générée par un Assistant Application ou que vous possédez des en-têtes précompilés, vous devez désactiver ou recompiler ces derniers avant de compiler les autres modules. Sinon, vous recevrez l'avertissement C4650 et le message d'erreur C2855. Vous pouvez désactiver les en-têtes précompilés en modifiant le paramètre **créer/utiliser des en-têtes précompilés** dans la boîte de dialogue **\<Project> Propriétés** (dossier **Propriétés de configuration** , sous-dossier **C/C++** , catégorie **en-têtes précompilés** ).

7. Dans le menu **Générer** , cliquez sur **Générer** pour régénérer les fichiers projet  qui sont obsolètes.

   Au lieu d'utiliser la technique décrite dans cette rubrique, vous pouvez définir des options individuelles pour chaque fichier en recourant à un makefile externe. Dans ce cas, pour lier avec les bibliothèques de débogage MFC, vous devez avoir défini l'indicateur [_DEBUG](/cpp/c-runtime-library/debug) pour chaque module. Si vous voulez utiliser des bibliothèques MFC en version Release, vous devez définir NDEBUG. Pour plus d'informations sur l'écriture de makefiles externes, consultez la [Référence NMAKE](/cpp/build/running-nmake).

   [Dans cette rubrique](#BKMK_In_this_topic)

## <a name="see-also"></a>Voir aussi
[Débogage du code natif](../debugger/debugging-native-code.md)