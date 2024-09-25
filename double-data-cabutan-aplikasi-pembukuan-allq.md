# Dobel Data Cabutan di aplikasi pembukuan allq

```php
$workareaId = 'workarea_id';
$cabutan = Cabutan::selectRaw('MIN(id)')->from('cabutans')->where('year', 5)->where('month_id', 3)->where('branch_id', 'branch_id')->where('workarea_id', $workareaId)->groupBy('day_id');
$duplicateIds = Cabutan::where('year', 5)->where('month_id', 3)->where('branch_id', 'branch_id')->where('workarea_id', $workareaId)->select('id')->whereNotIn('id', $cabutan)->pluck('id');
Cabutan::whereIn('id', $duplicateIds)->delete();
```
