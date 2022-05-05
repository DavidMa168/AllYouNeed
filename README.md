// Show report
Process.Start(new ProcessStartInfo(outputFile) { UseShellExecute = true });

// List<string> 用 Lambda 找出重複的部分
List<string> srNos = new List<string>();
var mults = srNos.GroupBy(c => c).Where(c => c.Count() > 1).Select(c => new { SRNo = c.Key });
if (mults.Count() > 0)
    {
        string strMult = string.Join(", ", mults);
        MessageBox.Show($"以下SR單號選超過1筆，{strMult}");
        return;
    }

items.GroupBy(e => e).ToDictionary(k => k.Key, v => v.Count());
    
    
