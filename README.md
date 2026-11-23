# Test

Set(varCampagne; First(Sort('Modele PAC Trim'; Campagne; SortOrder.Descending)).Campagne);;
ClearCollect(colPAC; Filter('Modele PAC Trim'; Campagne = varCampagne));;
ClearCollect(colSegments; {Seg: "Tous les segments"});;
Collect(colSegments; ForAll(Sort(Distinct(colPAC; SEGMENT); Value); {Seg: Value}))
