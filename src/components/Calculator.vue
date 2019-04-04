<template>
    <main>
        <div class="inputs">
            <h1>Freelance Rate Calculator</h1>
            <p>Fill out all the fields that apply to you and view the estimated hourly rate on the right. If the field doesn't apply to you, put a 0 in it instead.</p>
            <br><br>
            <div class="field">
                <label for="rent">Desired Salary</label>
                <input class="input" type="text" v-model="desiredSalary">
            </div>
            <div class="field">
                <label for="rent">Profit Margin Percentage (Usually 10-20%)</label>
                <input class="input" type="text" v-model="profitMarginPercentage">
            </div>
            <br>
            <h2>Yearly Expenses</h2>
            <div class="field">
                <label for="rent">Rent</label>
                <input class="input" type="text" v-model="rent">
            </div>
            <div class="field">
                <label for="rent">Telephone</label>
                <input class="input" type="text" v-model="phone">
            </div>
            <div class="field">
                <label for="rent">Internet</label>
                <input class="input" type="text" v-model="internet">
            </div>
            <div class="field">
                <label for="rent">Office Equipment</label>
                <input class="input" type="text" v-model="officeEquipment">
            </div>
            <div class="field">
                <label for="rent">Office Supplies</label>
                <input class="input" type="text" v-model="officeSupplies">
            </div>
            <div class="field">
                <label for="rent">Travel Expenses</label>
                <input class="input" type="text" v-model="travelExpenses">
            </div>
            <div class="field">
                <label for="rent">Advertising</label>
                <input class="input" type="text" v-model="advertising">
            </div>
            <div class="field">
                <label for="rent">Business Insurance</label>
                <input class="input" type="text" v-model="businessInsurance">
            </div>
            <div class="field">
                <label for="rent">Business License Fees</label>
                <input class="input" type="text" v-model="businessLicenseFees">
            </div>
            <div class="field">
                <label for="rent">Legal Fees</label>
                <input class="input" type="text" v-model="legalFees">
            </div>
            <div class="field">
                <label for="rent">Accounting Fees</label>
                <input class="input" type="text" v-model="accountingFees">
            </div>
            <div class="field">
                <label for="rent">Professional Memberships</label>
                <input class="input" type="text" v-model="memberships">
            </div>
            <br>
            <h2>Non Billable Days</h2>
            <p>Note: These offdays will count as normal 8hr days.</p>
            <div class="field">
                <label for="rent">Number of Holiday Days</label>
                <input class="input" type="text" v-model="holidays">
            </div>
            <div class="field">
                <label for="rent">Number of Sick Days</label>
                <input class="input" type="text" v-model="sickDays">
            </div>
            <div class="field">
                <label for="rent">Number of Vacation Days</label>
                <input class="input" type="text" v-model="vacationDays">
            </div>
            <div class="field">
                <label for="rent">Number of Travel Days</label>
                <input class="input" type="text" v-model="travelDays">
            </div>
            <!-- <p>{{ offdaysTotal }} days x 8 hours = {{ getNonBillableHours }} nonbillable hours</p> -->
            <br>
            <h2>Billable Hours</h2>
            <div class="field">
                <label for="rent">Avg hours worked per day</label>
                <input class="input" type="text" v-model="billableHoursPerDay">
            </div>
            <!-- <p>{{ getBillableHours }} billable hrs per week × {{ weeksInAYear }} weeks = {{(getBillableHours) * weeksInAYear}} billable hrs per year</p> -->
            <!-- <p>{{(getYearlyBillableHours)}} billable hrs - {{ getNonBillableHours }} nonbillable hrs = {{ getTotalBillableHours }} total billable hrs</p> -->
        </div>
        <div class="outputs">
            <!-- <h2>Outputs</h2> -->
            <!-- Billable Days -->
            <!-- <div class="output">
                <h3>Yearly Billable Days</h3>
                <h3>{{ desiredSalary }}</h3>
            </div> -->
            <!-- /Billable Days -->
            <!-- Weekly Billable Hours -->
            <!-- <div class="output">
                <h3>Weekly Billable Hours</h3>
                <h3>{{ desiredSalary }}</h3>
            </div> -->
            <!-- /Weekly Billable Hours -->
            <!-- Yearly Billable Hours -->
            <!-- <div class="output">
                <h3>Yearly Billable Hours</h3>
                <h3>{{ desiredSalary }}</h3>
            </div> -->
            <!-- /Yearly Billable Hours -->
            <!-- Salary -->
            <div class="output">
                <h3>Desired Salary</h3>
                <h3>{{ desiredSalary }}</h3>
            </div>
            <!-- /Salary -->
            <!-- Expenses -->
            <div class="output">
                <h3>Expenses</h3>
                <h3>{{ getTotalExpenses }}</h3>
            </div>
            <!-- /Expenses -->
            <!-- Total -->
            <div class="output">
                <h3>Salary + Expenses</h3>
                <h3>{{ getSalaryExpenses }}</h3>
            </div>
            <!--  Total -->
            <!-- Profit Margin Total -->
            <div class="output">
                <h3>Profit Margin of {{profitMarginPercentage}}%</h3>
                <h3>{{ getProfitMarginTotal }}</h3>
            </div>
            <!-- /Profit Margin Total -->
            <!-- Grand Total -->
            <div class="output">
                <h3>Grand Total</h3>
                <h3>{{ getGrandTotal }}</h3>
            </div>
            <!-- /Grand Total -->
            <br>
            <br>
            <!-- Hour Rate -->
            <div class="output">
                <h3>Hourly Rate</h3>
                <h3>{{ getHourlyRate }}</h3>
            </div>
            <!-- /Hour Rate -->
        </div>
    </main>
</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
        // Normal Variables
        normalHours: 8,
        weeksInAYear: 52,
        // Salary
        desiredSalary: 0,
        profitMarginPercentage: 0,
        // Expenses
        rent: 0,
        phone: 0,
        internet: 0,
        officeEquipment: 0,
        officeSupplies: 0,
        travelExpenses: 0,
        advertising: 0,
        businessInsurance: 0,
        businessLicenseFees: 0,
        legalFees: 0,
        accountingFees: 0,
        memberships: 0,
        // Billable Days
        holidays: 0,
        sickDays: 0,
        vacationDays: 0,
        travelDays: 0,
        offdays: 0,
        nonBillableHours: 0,
        // Billable Hours
        billableHoursPerDay: 0,
        billableHoursPerWeek: 0,
        totalBillableHours: 0,
        // Outputs
        expensesTotal: 0,
        total: 0,
        grandTotal: 0,
        profitMarginTotal: 0,
        hourlyRate: 0
    } 
  },
  computed: {
        getOffDaysTotal () {
            let total = parseInt(this.holidays) + parseInt(this.sickDays) + parseInt(this.vacationDays) + parseInt(this.travelDays);
            return this.offdays = total;
        },
        getNonBillableHours () {
            return (this.getOffDaysTotal * this.normalHours);
        },
        getBillableHours () {
            return this.billableHoursPerDay * 5;
        },
        getYearlyBillableHours () {
            return this.getBillableHours * 52;
        },
        getTotalBillableHours () {
            return (this.getYearlyBillableHours - this.getNonBillableHours);
        },
        getTotalExpenses () {
            let total = parseInt(this.rent) + parseInt(this.phone) + parseInt(this.internet) + parseInt(this.officeEquipment) + parseInt(this.officeSupplies) + parseInt(this.travelExpenses) + parseInt(this.advertising) + parseInt(this.businessInsurance) + parseInt(this.businessLicenseFees) + parseInt(this.legalFees) + parseInt(this.accountingFees) + parseInt(this.memberships);
            return total;
        },
        getSalaryExpenses () {
            return parseInt(this.getTotalExpenses) + parseInt(this.desiredSalary);
        },
        getProfitMargin () {
            // 15 / 100 = 0.15
            return (parseInt(this.profitMarginPercentage) / 100);//0.15
        },
        getProfitMarginTotal () {
            // 119,000 * 0.15 = 17,850
            return this.getSalaryExpenses * this.getProfitMargin;
        },
        getGrandTotal () {
            // Salary + Expenses + Profit Margin
            return this.getSalaryExpenses + this.getProfitMarginTotal;
        },
        getHourlyRate () {
            let grandTotal = this.getGrandTotal;
            let billableHours = this.getTotalBillableHours;
            return (grandTotal / billableHours).toFixed(2);
        }
  }
};
</script>

<style lang="scss">
// Pulled some styles from Bulma
h1 {
    margin-bottom: 0.3rem;
}
p {
    margin-top: 0;
}
main {
    display: flex;
    max-width: 1140px;
    margin: 0 auto;
}
.inputs {
    display: flex;
    flex-direction: column;
    width: 60%;
    padding: 1.5rem 2.5rem 1rem 0;
}
.outputs {
    width: 40%;
    padding: 1.5rem 2.5rem;
}
.output {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
// Form
.button, .file-cta, .file-name, .input, .pagination-ellipsis, .pagination-link, .pagination-next, .pagination-previous, .select select, .textarea {
    -moz-appearance: none;
    -webkit-appearance: none;
    align-items: center;
    border: 1px solid transparent;
    border-radius: 4px;
    box-shadow: none;
    display: inline-flex;
    font-size: 1rem;
    height: 2.25em;
    justify-content: flex-start;
    line-height: 1.5;
    padding-bottom: calc(.375em - 1px);
    padding-left: calc(.625em - 1px);
    padding-right: calc(.625em - 1px);
    padding-top: calc(.375em - 1px);
    position: relative;
    vertical-align: top;
}
.field {
    margin-bottom: 1.6rem;
}
.input, .textarea {
    background-color: #fff;
    border-color: #dbdbdb;
    border-radius: 4px;
    color: #363636;
    max-width: 100%;
    width: 100%;
}
label {
    display: flex;
    font-size: 1.2rem;
    margin-bottom: 0.5rem;
}
</style>