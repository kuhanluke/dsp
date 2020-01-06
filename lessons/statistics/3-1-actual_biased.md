[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

    import nsfg
    import thinkstats2
    import thinkplot

    resp = nsfg.ReadFemResp()

    under18 = resp.numkdhh


    def BiasPmf(pmf, label=None):
        new_pmf = pmf.Copy(label=label)

        for x, p in pmf.Items():
            new_pmf.Mult(x, x)

        new_pmf.Normalize()
        return new_pmf


    pmf = thinkstats2.Pmf(under18, label='actual')
    biased_pmf = BiasPmf(pmf, label='biased')
    thinkplot.PrePlot(2)
    thinkplot.Pmfs([pmf, biased_pmf])
    thinkplot.Show(xlabel='children under 18', ylabel='PMF')
    

![Figure_1](https://user-images.githubusercontent.com/59043029/71825239-0ad65100-3061-11ea-9b65-df7ca32ad2c8.png)
