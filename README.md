# Test

Set(varCampagne; First(Sort('Modele PAC Trim'; Campagne; SortOrder.Descending)).Campagne);;
Set(varDomaine; Lower(Last(Split(User().Email; "@")).Value));;
ClearCollect(colMesETB; Filter('Habilitations PAC'; Title = User().Email || Title = varDomaine));;
Set(varToutVoir; CountIf(colMesETB; ETB = "*") > 0);;
Clear(colPAC);;
If(varToutVoir;
    Collect(colPAC; Filter('Modele PAC Trim'; Campagne = varCampagne));
    ForAll(colMesETB As mon; Collect(colPAC; Filter('Modele PAC Trim'; Campagne = varCampagne; ETB = mon.ETB)))
);;
ClearCollect(colSegments; {Seg: "Tous les segments"});;
Collect(colSegments; ForAll(Sort(Distinct(colPAC; SEGMENT); Value); {Seg: Value}))